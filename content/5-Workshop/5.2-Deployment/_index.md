---
title: "Deployment Process"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---
# Deployment Process

## Yahoo Finance API

Yahoo Finance là nguồn dữ liệu thị trường chính của hệ thống. Hệ thống sử dụng Yahoo Finance để lấy dữ liệu giá cổ phiếu như giá mở cửa, giá cao nhất, giá thấp nhất, giá đóng cửa, khối lượng giao dịch và lịch sử giá theo từng khung thời gian.

## Deployment Backend

### Amazon S3 - Raw Data Storage

Bucket được tạo: [production-stock-raw-data-finance](https://ap-southeast-1.console.aws.amazon.com/s3/buckets/production-stock-raw-data-finance?region=ap-southeast-1)

Amazon S3 dùng để lưu trữ dữ liệu thô lấy từ Yahoo Finance. Việc lưu raw data giúp hệ thống có thể kiểm tra lại dữ liệu đầu vào, tái xử lý khi cần và tách biệt bước thu thập dữ liệu với bước phân tích.

![S3 raw data bucket](/images/5-Workshop/stock-project/03-s3-raw-data.png)

### Amazon SQS

Queues được tạo:

- `stock-processing-dlq`
- `stock-processing-queue`

Amazon SQS đóng vai trò hàng đợi trung gian giữa Ingestion Lambda và Processing Lambda. SQS giúp hệ thống xử lý bất đồng bộ, tránh việc Lambda thu thập dữ liệu phải chờ quá trình phân tích hoàn tất. Khi có dữ liệu mới, message sẽ được đưa vào SQS để Processing Lambda xử lý sau.

![SQS queues](/images/5-Workshop/stock-project/04-sqs-queues.png)

Dead-letter queue được cấu hình để lưu các message xử lý lỗi sau số lần retry giới hạn.

![SQS dead-letter queue](/images/5-Workshop/stock-project/05-sqs-dlq.png)

### AWS Lambda

Functions được tạo:

- `production-stock-ingestion`
- `production-stock-processing`

Runtime sử dụng: Node.js 22.x.

Ingestion Lambda có nhiệm vụ nhận yêu cầu phân tích cổ phiếu từ API Gateway, gọi Yahoo Finance để lấy dữ liệu thị trường, chuẩn hóa dữ liệu và lưu dữ liệu thô vào S3. Sau đó Lambda gửi message vào SQS để kích hoạt bước xử lý tiếp theo.

Processing Lambda là thành phần xử lý chính của hệ thống. Lambda này đọc dữ liệu từ S3 thông qua message trong SQS, sau đó tính toán các chỉ báo kỹ thuật như RSI, MACD, MA20, MA50 và Volume. Sau khi có chỉ báo kỹ thuật, Lambda gửi dữ liệu đã tính sang Amazon Bedrock để AI tạo phân tích và khuyến nghị.

![Lambda functions](/images/5-Workshop/stock-project/06-lambda-functions.png)

### AWS IAM Role

IAM Role được cấu hình để Lambda có quyền truy cập S3, SQS, DynamoDB, SES và Amazon Bedrock theo đúng nhu cầu xử lý của hệ thống.

![IAM policy for S3 SQS DynamoDB](/images/5-Workshop/stock-project/07-iam-policy-s3-sqs-dynamodb.png)

![IAM policy for SES and Bedrock](/images/5-Workshop/stock-project/08-iam-policy-ses-bedrock.png)

![Bedrock invocation policy](/images/5-Workshop/stock-project/09-bedrock-policy.png)

### AWS KMS

KMS được sử dụng để mã hóa dữ liệu nhạy cảm và tăng mức độ an toàn cho dữ liệu lưu trữ trong hệ thống.

![KMS key list](/images/5-Workshop/stock-project/10-kms-key-list.png)

### Amazon DynamoDB

Table được tạo: `Stock_reports_1`.

Key design:

- Partition key: `PK` - String
- Sort key: `SK` - String

DynamoDB dùng để lưu kết quả phân tích cuối cùng, bao gồm mã cổ phiếu, khung thời gian, chỉ báo kỹ thuật, khuyến nghị AI, điểm tin cậy, lý do phân tích và trạng thái phê duyệt của trader. Đây là nơi Dashboard truy vấn dữ liệu để hiển thị báo cáo cho người dùng.

![DynamoDB tables](/images/5-Workshop/stock-project/11-dynamodb-tables.png)

Dữ liệu trong DynamoDB được mã hóa bằng KMS.

![DynamoDB KMS encryption](/images/5-Workshop/stock-project/12-dynamodb-kms-encryption.png)

## Deployment Frontend

### Amazon S3 - Frontend Hosting

Bucket được tạo: `stock-frontend-finance`.

Ngoài chức năng lưu trữ dữ liệu thô ở Backend, Amazon S3 còn được sử dụng để lưu trữ mã nguồn giao diện Web dưới dạng Static Website Hosting. Các tệp HTML, CSS, JavaScript và các tài nguyên tĩnh khác được lưu trong S3 và được CloudFront phân phối đến người dùng. Cách triển khai này giúp giảm chi phí vận hành, không cần quản lý máy chủ Web và dễ dàng cập nhật phiên bản giao diện mới.

![S3 frontend bucket](/images/5-Workshop/stock-project/13-s3-frontend.png)

### Amazon CloudFront and AWS WAF

Amazon CloudFront là dịch vụ CDN được sử dụng để phân phối giao diện Web của hệ thống đến người dùng với tốc độ nhanh hơn. CloudFront lưu các nội dung tĩnh như HTML, CSS và JavaScript tại các Edge Location gần người dùng, từ đó giảm độ trễ khi truy cập và giảm tải cho S3. Ngoài ra, CloudFront còn hỗ trợ HTTPS và tích hợp với AWS WAF để tăng cường bảo mật cho hệ thống.

AWS WAF được triển khai trước CloudFront nhằm bảo vệ ứng dụng Web khỏi các cuộc tấn công phổ biến trên Internet. WAF cho phép xây dựng các luật để lọc và chặn các request độc hại như SQL Injection, Cross-Site Scripting, bot hoặc các request có tần suất bất thường. Nhờ đó, hệ thống giảm thiểu nguy cơ bị khai thác lỗ hổng và nâng cao mức độ an toàn khi cung cấp dịch vụ cho người dùng.

![CloudFront and WAF](/images/5-Workshop/stock-project/14-cloudfront-waf.png)

### Amazon Cognito

Amazon Cognito dùng để xác thực người dùng đăng nhập vào hệ thống. Chỉ những người dùng hợp lệ như trader hoặc admin mới có thể truy cập Dashboard, xem báo cáo phân tích và thực hiện thao tác phê duyệt hoặc từ chối khuyến nghị.

![Cognito user pool](/images/5-Workshop/stock-project/15-cognito-user-pool.png)

### Amazon API Gateway

API Gateway đóng vai trò là cổng giao tiếp giữa Frontend và Backend. Khi người dùng thao tác trên Dashboard, request sẽ được gửi đến API Gateway, sau đó API Gateway chuyển tiếp request đến các Lambda tương ứng.

API được tạo: `Ingestion-lambda_API`.

![API Gateway resources](/images/5-Workshop/stock-project/16-api-gateway.png)

### Amazon Bedrock Quota

Amazon Bedrock được sử dụng để phân tích dữ liệu kỹ thuật đã được backend tính toán. Bedrock không trực tiếp lấy dữ liệu thị trường và không dùng tin tức. Nó chỉ nhận các chỉ số như RSI, MACD, MA và giá cổ phiếu để tạo ra khuyến nghị như "MUA MẠNH", "BÁN MẠNH" hoặc "THEO DÕI", kèm theo điểm tin cậy và lý do phân tích.

![Bedrock request quota](/images/5-Workshop/stock-project/17-bedrock-quota.png)

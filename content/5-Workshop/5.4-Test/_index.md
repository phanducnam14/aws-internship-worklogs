---
title: "Test"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---
# Test

## Đăng nhập bằng Cognito

Người dùng đăng nhập vào Dashboard thông qua Amazon Cognito. Do hệ thống đã có user nội bộ nên sau khi bấm đăng nhập bằng Cognito, trader có thể truy cập Dashboard ngay.

![Cognito login screen](/images/5-Workshop/stock-project-test/01-cognito-login.png)

## Kiểm tra Dashboard ban đầu

Ở trạng thái ban đầu, Dashboard chỉ hiển thị mã FPT trong danh sách theo dõi.

![Dashboard only FPT](/images/5-Workshop/stock-project-test/02-dashboard-fpt.png)

## Phân tích mã cổ phiếu khác

Trader chuyển sang màn hình phân tích, chọn mã cổ phiếu `VNM`, chọn khung thời gian ngày và bấm **Phân tích**.

![Analyze VNM stock](/images/5-Workshop/stock-project-test/03-analysis-vnm.png)

## Kiểm tra luồng Ingestion và Processing

Sau khi phân tích thành công, Ingestion Lambda gọi Yahoo Finance API để lấy dữ liệu thị trường. Dữ liệu thô được lưu vào S3 theo từng mã cổ phiếu, sau đó message được đẩy vào SQS để kích hoạt Processing Lambda.

![S3 Yahoo Finance raw data](/images/5-Workshop/stock-project-test/04-s3-yahoo-finance.png)

Processing Lambda lấy message từ SQS, đọc dữ liệu trong S3 và xử lý các thông số kỹ thuật như MA20, MACD, RSI và Volume.

![SQS message status](/images/5-Workshop/stock-project-test/05-sqs-after-ingestion.png)

Trên Dashboard, quá trình phân tích trả về trạng thái thành công và thông báo đã lưu raw JSON từ Yahoo Finance.

![Dashboard analysis success](/images/5-Workshop/stock-project-test/06-dashboard-analysis-success.png)

SQS còn `0` message vì Processing Lambda đã xử lý message từ S3 qua SQS.

## Kiểm tra DynamoDB

Sau khi Processing Lambda xử lý xong, DynamoDB lưu lại mã cổ phiếu và kết quả phân tích. Trong lần test này, table `Stock_reports_1` đã có thêm dữ liệu cho `TICKER#VNM`.

![DynamoDB VNM item](/images/5-Workshop/stock-project-test/07-dynamodb-vnm.png)

## Kiểm tra Dashboard sau khi phân tích

Dashboard đã thể hiện mã cổ phiếu thành công với các thông số như MA20, MACD, RSI và confidence. Hiện có 3 mã vì hệ thống đã phân tích 3 mã cổ phiếu.

![Dashboard three stocks](/images/5-Workshop/stock-project-test/08-dashboard-three-stocks.png)

## Kiểm tra log Processing Lambda

CloudWatch Logs được dùng để kiểm tra Processing Lambda. Log cho thấy flow đã chạy thành công và các bước xử lý theo logic kiến trúc đã thiết kế.

![Processing Lambda success logs](/images/5-Workshop/stock-project-test/09-processing-logs-success.png)

## Lỗi Bedrock quota

Trong quá trình test, Bedrock gặp lỗi quota: `Too many tokens per day, please trying again.`

![Bedrock token quota error](/images/5-Workshop/stock-project-test/10-bedrock-token-error.png)

Do Bedrock bị giới hạn token, các cổ phiếu đang nằm ở mức confidence `68`, thấp hơn ngưỡng `75` để Bedrock có thể tạo phân tích đầy đủ và gửi email. Khi lỗi xảy ra, hệ thống fallback về dữ liệu mock với confidence `68` để vẫn có dữ liệu hiển thị trên Dashboard.

![Confidence fallback](/images/5-Workshop/stock-project-test/11-confidence-fallback.png)

## Cách khắc phục

Cách khắc phục là request quota cho model đang sử dụng, cụ thể là Claude 3.5 V2. Sau khi quota được tăng, Bedrock có thể xử lý chỉ số kỹ thuật và tạo báo cáo phân tích đầy đủ trên Dashboard.

![Bedrock quota request and dashboard](/images/5-Workshop/stock-project-test/12-bedrock-quota-and-dashboard.png)

Trader sẽ là người kiểm duyệt báo cáo cuối cùng. Nếu có tín hiệu `MUA MẠNH` hoặc `BÁN MẠNH`, trader cần duyệt trước khi hệ thống gửi báo cáo qua Gmail cho khách hàng.

Hiện tại chưa có tín hiệu mua mạnh hoặc bán mạnh nào cần trader duyệt.

![Trader review empty](/images/5-Workshop/stock-project-test/13-trader-review-empty.png)

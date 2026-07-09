---
title: "Future Improvements"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---
# Future Improvements

## Các bước cải tiến trong tương lai

### 1. Mở rộng nguồn dữ liệu

Hiện tại hệ thống chỉ sử dụng Yahoo Finance. Trong tương lai có thể bổ sung thêm các nguồn dữ liệu khác để đối chiếu giá, tăng độ tin cậy và hỗ trợ dữ liệu gần thời gian thực hơn.

### 2. Cải thiện mô hình phân tích AI

Amazon Bedrock hiện chỉ phân tích dựa trên chỉ báo kỹ thuật. Sau này có thể mở rộng thêm nhiều chỉ báo hơn như Bollinger Bands, Stochastic, ADX hoặc ATR để AI có thêm dữ liệu đầu vào và đưa ra phân tích chính xác hơn.

### 3. Bổ sung cảnh báo thời gian thực

Hệ thống có thể thêm chức năng cảnh báo khi giá cổ phiếu vượt ngưỡng, RSI quá mua/quá bán hoặc MACD đảo chiều. Khi có tín hiệu quan trọng, hệ thống có thể gửi thông báo cho trader hoặc khách hàng.

### 4. Hoàn thiện quy trình quản trị người dùng

Có thể phân quyền rõ hơn giữa Admin, Trader và Customer. Ví dụ Admin quản lý người dùng, Trader phê duyệt khuyến nghị, Customer chỉ nhận báo cáo hoặc xem lịch sử khuyến nghị.

### 5. Tăng cường bảo mật

Hệ thống có thể bổ sung thêm các lớp bảo mật như CloudWatch Alarm, AWS WAF Rules nâng cao, giới hạn request theo IP, audit log bằng CloudTrail và mã hóa dữ liệu nhạy cảm bằng KMS.

### 6. Tối ưu chi phí và hiệu năng

Có thể theo dõi chi phí qua AWS Cost Explorer, tối ưu số lần gọi Bedrock, giảm token đầu vào, cache dữ liệu cổ phiếu và điều chỉnh timeout/memory của Lambda để giảm chi phí vận hành.

### 7. Cải thiện Dashboard

Dashboard có thể được nâng cấp thêm biểu đồ trực quan hơn, bộ lọc theo mã cổ phiếu, trạng thái phê duyệt, độ tin cậy, khung thời gian và lịch sử các lần phân tích trước đó.

### 8. Bổ sung CI/CD

Trong tương lai có thể triển khai CI/CD bằng GitHub Actions hoặc AWS CodePipeline để tự động build, test và deploy frontend/backend, giúp quá trình cập nhật hệ thống an toàn và chuyên nghiệp hơn.

### 9. Mở rộng khả năng scale

Khi số lượng mã cổ phiếu và người dùng tăng lên, hệ thống có thể tối ưu batch processing, tăng concurrency cho Lambda, cấu hình DLQ cho SQS và thiết lập retry policy rõ ràng để đảm bảo hệ thống hoạt động ổn định.

### 10. Thêm cơ chế đánh giá độ chính xác

Sau khi hệ thống đưa ra khuyến nghị, có thể lưu lại kết quả thực tế của cổ phiếu sau một khoảng thời gian để đánh giá khuyến nghị đúng hay sai. Từ đó cải thiện logic tính điểm và chất lượng phân tích của hệ thống.

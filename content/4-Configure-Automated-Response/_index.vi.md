+++
title = "Cấu hình phản hồi tự động"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Cấu hình phản hồi tự động

Trong phần này, bạn sẽ học cách tạo các phát hiện mẫu bằng **GuardDuty** và sử dụng chúng làm đầu vào cho quy trình phản hồi sự cố tự động.

Trong môi trường, có một instance _"RedTeam"_ sẽ tạo ra các phát hiện từ **GuardDuty**.

1. Truy cập vào **GuardDuty**, chọn **Settings**.
2. Trong phần _Findings export options_, tần suất cập nhật nên là mỗi 15 phút nếu bạn sử dụng CloudFormation template. (Nếu chưa được thiết lập, hãy nhấn _Edit_ và chỉnh tần suất cập nhật thành mỗi 15 phút).

![GuardDuty](../../images/4/GuardDuty_frequency.png?width=90pc)

3. Sau đó chọn mục **Findings**.

{{% notice note %}}
Bạn cần chờ một lúc để các phát hiện được tạo ra, ngoài ra một số dịch vụ khác đang chạy có thể làm tăng chi phí. Nếu không muốn chờ, bạn có thể bỏ qua phần này (optional). Dưới đây là ví dụ kết quả mà bạn có thể thấy.
{{% /notice %}}

![GuardDuty](../../images/4/GuardDuty_findings.png?width=90pc)


#### Kiểm thử phản hồi tự động

Để kiểm thử phản hồi tự động, bạn có thể:

1. Chờ instance RedTeam tạo ra sự kiện, vì nó đang sử dụng [GuardDuty tester scripts](https://github.com/awslabs/amazon-guardduty-tester)

2. Bạn cũng có thể tự tạo một instance Windows mới, tạo một Security Group cho phép truy cập RDP (cổng 3389) từ địa chỉ IP của bạn, và mô phỏng hành vi kết nối độc hại bằng cách:

   - Cài đặt [TOR Browser](https://www.torproject.org/download/)
   - Kết nối tới các mining pool như `pool.minergate.com`

3. Hoặc tạo một instance Linux mới, với Security Group cho phép SSH (cổng 22) từ địa chỉ IP của bạn, và gọi tới domain giả mạo đã được thêm vào threat intelligence feed (dùng để kiểm thử phát hiện Command & Control) với lệnh sau:
```
dig GuardDutyC2ActivityB.com any
```

4. Chờ một vài phút (có thể mất đến 20 phút) để **GuardDuty** tạo ra các phát hiện.

{{% notice note %}}
Nếu bạn chọn dùng instance Linux, có thể kết nối thông qua EC2 Instance Connect để truy cập terminal, hoặc dùng SSH.
{{% /notice %}}

{{% notice note %}}
Để kết nối vào instance RedTeam, bạn có thể sử dụng Systems Manager Session Manager, tuy nhiên cần gán instance profile cho SSM và khởi động lại instance.
{{% /notice %}}

+++
title = "Phản hồi bằng Step Function"
date = 2025
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

### Cấu hình phản hồi bằng Step Function

Trong phần này, bạn sẽ học cách triển khai hành động phản hồi sự cố tự động thông qua một workflow được xây dựng bằng **Step Functions**. Những lợi ích của phương pháp này bao gồm:

- **Không bị giới hạn thời gian** khi thực hiện các hành động.
- Hầu hết các lệnh gọi API của các dịch vụ AWS đều được hỗ trợ và có thể gọi trực tiếp mà không cần viết code.
- Định nghĩa quy trình làm việc bằng đồ thị.
- Kiểm soát tốt hơn các nhánh xử lý khác nhau.

Các bước chúng ta sẽ thực hiện trong phương án này:

- Triển khai một **CloudFormation** template để tạo tất cả các tài nguyên cần thiết.
- Xác nhận đăng ký SNS để nhận _thông báo qua email_.
- Kiểm thử **State Machine**.
- Tạo một **EventBridge** rule để gọi _State Machine_ dựa trên các phát hiện từ **GuardDuty**.

Kiến trúc của phương án này như sau:
![SF](../../../images/1/Workshop_Step_Function.jpg?width=90pc)

Và đồ thị workflow của Step Function như sau:
![SF](../../../images/1/Step_Functions_workflow.png)

Giải thích ngắn gọn về workflow được trình bày:

1. Kiểm tra xem có _instance ID_ trong phát hiện từ **GuardDuty** hay không.
2. Dựa trên mức độ nghiêm trọng (**severity**) của phát hiện từ **GuardDuty**:

   - Nếu **severity từ 8 trở lên**, một _SNS notification_ sẽ được gửi tới email đã đăng ký (email bạn đã nhập khi triển khai CloudFormation).
   - Nếu **severity nhỏ hơn 8**, một email _Manual Approval_ sẽ được gửi đến email đã đăng ký:
     - Nếu _Manual Approval_ bị **từ chối**, workflow sẽ kết thúc và không thực hiện hành động nào.
     - Nếu _Manual Approval_ được **chấp thuận**, các hành động sau sẽ được thực hiện.

3. Bật chế độ bảo vệ khỏi bị terminate trên EC2 instance.
4. Thay đổi hành vi khi shutdown của instance.
5. Áp dụng Security Group _ForensicSG_ cho instance.
6. Gán tag _isolated_ cho instance.
7. Workflow kết thúc.

Nếu bạn đã đọc xong, hãy chuyển sang bước tiếp theo là [Triển khai CloudFormation stack](3.2.1-Deploy-the-CloudFormation-stack).

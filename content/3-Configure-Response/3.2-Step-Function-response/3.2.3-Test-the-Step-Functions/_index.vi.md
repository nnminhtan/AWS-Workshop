+++
title = "Test Step Functions"
date = 2025
weight = 3
chapter = false
pre = "<b>3.2.3. </b>"
+++

<!-- #### Kiểm thử Lambda Function: -->

Trong bước này, chúng ta sẽ kiểm thử Step Functions đã được tạo trước đó.

1. Truy cập vào dịch vụ **Step Functions** và trong mục **State machines**, chọn tên của state machine mới được tạo _**PREFIX_StateMachine**_.

   ![Test SF](../../../../images/3/3.2/3.2.3/State_machine.png?width=90pc)

2. Chọn **Start execution**

   ![Test SF](../../../../images/3/3.2/3.2.3/Start_execution.png?width=90pc)

    - Sao chép đoạn JSON bên dưới và dán vào phần _Input_, tuy nhiên bạn cần chỉnh sửa vài giá trị trước khi chạy.

    ```json
    {
        "version": "0",
        "id": "cd2d702e-ab31-411b-9344-793ce56b1bc7",
        "detail-type": "GuardDuty Finding",
        "source": "aws.guardduty",
        "account": "<<Account ID>>",
        "time": "1970-01-01T00:00:00Z",
        "region": "us-east-1",
        "resources": [],
        
        "detail": {
            "schemaVersion": "2.0",
            "accountId": "<<Account ID>>",
            "region": "us-east-1",
            "partition": "aws",
            "id": "b0baa89de4ab301f8d0a8c9a3dfd5726",
            "arn": "arn:aws:guardduty:us-east-1:<<Account ID>>:detector/feb3c048238f682b8902532ec100b3fb/finding/b0baa89de4ab301f8d0a8c9a3dfd5726",
            "title": "Bitcoin-related domain name queried by EC2 instance <<Instance ID>>.",
            "type": "CryptoCurrency:EC2/BitcoinTool.B!DNS",
            "severity": 8,
            "resource": {
                "instanceDetails": {
                    "instanceId": "<<Instance ID>>"
                }
            }
        }
    }
    ```

    - Thay thế **Account ID** bằng tài khoản của bạn.
    - Thay thế **Instance ID** bằng ID của instance "BasicLinuxTarget" được triển khai bởi CloudFormation template. (Xem hình dưới để biết cách tìm _Instance ID_).

    ![Test SF](../../../../images/3/3.1/3.1.3/Create_test_event_InstanceID.png?width=90pc)

    - Sau khi thay thế đầy đủ **Account ID** và **Instance ID**.

    ![Test SF](../../../../images/3/3.2/3.2.3/Start_execution_modification.png?width=90pc)

    - Kiểm tra trạng thái _trước khi thực thi_: vào **EC2 console** để kiểm tra trạng thái hiện tại của instance **"BasicLinuxTarget"**

    {{% notice note %}}
    Bạn có thể trả lời các câu hỏi sau không?

        • Nó đang sử dụng Security Group nào?
        • Nó có các tag nào?
        • Có snapshot nào liên quan đến instance này không?
    {{% /notice %}}

    - Nhấn nút _Start execution_, rồi kiểm tra lại trạng thái _sau khi thực thi_ của instance **"BasicLinuxTarget"**

    {{% notice note %}}
    Bạn có thể trả lời các câu hỏi sau không?

        • Security Group có thay đổi không?
        • Các tag có thay đổi không?
        • Có Snapshot mới nào được tạo ra không?
        • Đăng nhập bằng trình duyệt khác hoặc chế độ riêng tư, sử dụng liên kết trên IAM Dashboard (như hình bên dưới) để kiểm tra xem bạn có thể xóa EC2 bằng người dùng IAM testuser đã tạo ở bước cài đặt không.
        
            • Bạn có thể xóa được instance không?
    {{% /notice %}}

   ![Test SF](../../../../images/3/3.1/3.1.3/testuser_signin.png?width=90pc)

   - Khi bạn sử dụng _testuser_ để cố gắng xóa instance **"BasicLinuxTarget"**, bạn sẽ thấy lỗi như hình dưới.

   ![Test SF](../../../../images/3/3.1/3.1.3/testuser_delete.png?width=90pc)

3. Kiểm thử State Machine với mức độ nghiêm trọng (severity) khác
   - Làm lại các bước như trên nhưng thay đổi giá trị biến **severity** trong JSON từ `8` thành `7`.
     - Quy trình hoạt động có giống như trước không?
     - Điều gì đã thay đổi?

Khi bạn đã hoàn thành tất cả các bước, hãy tiếp tục sang phần tiếp theo của Workshop là [Tạo EventBridge Rule](../3.2.4-Create-EventBridge-Rule)

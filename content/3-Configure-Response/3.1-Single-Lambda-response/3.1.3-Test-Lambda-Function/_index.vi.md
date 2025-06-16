+++
title = "Test Lambda Function"
date = 2025
weight = 3
chapter = false
pre = "<b>3.1.3. </b>"
+++

<!-- #### Test Lambda Function: -->

Trong bước này, chúng ta sẽ kiểm thử Lambda Function đã tạo ở bước trước.

1. Xem lại phần comment trong code để hiểu các bước hoạt động.

   - Xem qua các bước chính trong code. Lưu ý: đây chỉ là ví dụ, bạn có thể thêm nhiều hành động khác.
   - Code có nhiều hàm print giúp bạn dễ dàng theo dõi trên CloudWatch Logs, hoặc bạn có thể giữ là comment nếu muốn.

2. Tạo **test event** cho Lambda function

   - Trong cùng trang _Function code editor_,  
   - Chọn **Test**, panel **Create new test event** sẽ mở ra, nhấn vào đó.

   ![Test Lambda](../../../../images/3/3.1/3.1.3/Create_test_event.png?width=90pc)

   - Panel _Create new test event_ sẽ mở, đặt tên test event là: `GuardDutyViaCWE`.
   - Dán JSON test event vào _Event JSON_, cần edit lại vài phần trước khi chạy được:
     - Thay `<<Account ID>>` bằng AWS Account của bạn.
     - Thay `<<Instance ID>>` bằng ID instance BasicLinuxTarget đã deploy (bạn có thể tìm ID như hình).

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
            "type": "UnauthorizedAccess:EC2/TorClient",
            "resource": {
                "instanceDetails": {
                    "instanceId": "<<Instance ID>>"
                }
            }
        }
    }
    ```

   ![Test Lambda](../../../../images/3/3.1/3.1.3/Create_test_event_InstanceID.png?width=90pc)

   - Sau khi chỉnh sửa xong, nhấn **Save**.

   ![Test Lambda](../../../../images/3/3.1/3.1.3/Create_test_event_modification.png?width=90pc)

   - Kiểm tra trạng thái instance **BasicLinuxTarget** trên EC2 console trước khi chạy test.
  
   ```
   Bạn có thể trả lời những câu hỏi sau không?

      • Instance đang dùng Security Group nào?.
      • Instance có những tag gì?.
      • Có snapshot nào liên quan đến instance không?.
   ```
   
   - Chạy test event vừa tạo và kiểm tra trạng thái instance **BasicLinuxTarget** sau khi chạy.

   ![Test Lambda](../../../../images/3/3.1/3.1.3/Test_event.png?width=90pc)

   ```
   Bạn có thể trả lời:

      • Security Group đã thay đổi chưa?
      • Tag đã thay đổi chưa?
      • Snapshot mới được tạo chưa?
      • Dùng trình duyệt khác hoặc chế độ ẩn danh, đăng nhập bằng user IAM `testuser` (đã tạo ở phần Setup), thử xóa instance BasicLinuxTarget.

         • Bạn có xóa được instance không?
   ```

   ![Test Lambda](../../../../images/3/3.1/3.1.3/testuser_signin.png?width=90pc)

   - Khi dùng user _testuser_ xóa instance **BasicLinuxTarget**, bạn sẽ gặp lỗi như hình dưới.

   ![Test Lambda](../../../../images/3/3.1/3.1.3/testuser_delete.png?width=90pc)

Khi hoàn thành, tiếp tục bước tiếp theo trong Workshop là [Tạo EventBridge Rule](../3.1.4-Create-EventBridge-Rule).

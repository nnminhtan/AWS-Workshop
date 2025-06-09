+++
title = "Xoá tài nguyên"
date = 2021-06-08T18:57:03+07:00
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

#### Xoá tài nguyên

Để tránh phát sinh chi phí không cần thiết cho tài khoản của bạn, chúng tôi khuyến nghị bạn nên xoá các tài nguyên đã được tạo trong suốt quá trình thực hiện workshop này. Nếu bạn muốn giữ lại để xem xét sau, hãy đảm bảo xoá tài nguyên khi hoàn tất.

{{% notice note %}}
Lưu ý rằng bạn cần xoá một số tài nguyên thủ công **trước khi xoá các CloudFormation stack**, vì vậy vui lòng **_thực hiện các bước sau theo thứ tự_**.
{{% /notice %}}

1. Tắt _termination protection_ cho các **EC2 instances** liên quan.
   - Mở **EC2 console**.
   - Chọn instance cần xoá.
   - Nhấn vào **Actions**, chọn **Instance settings**, sau đó thay đổi **termination protection**.

   ![CleanUp](/images/5/Instance_delete_1.png?width=90pc)

   - Bỏ chọn mục **Enable checkbox**, nhấn **Save**.

   ![CleanUp](/images/5/Instance_delete_2.png?width=90pc)

2. Xoá **CloudFormation stack**.
   - Truy cập **CloudFormation console**.
   - Chọn stack phù hợp (lưu ý rằng tuỳ thuộc vào phản hồi tự động bạn đã triển khai, có thể có 2 stack và 1 nested stack).
   - Nhấn **Delete**.

   ![CleanUp](/images/5/Delete_stack.png?width=90pc)

{{% notice warning %}}
Đảm bảo rằng trạng thái stack sau khi xoá là **DELETE_COMPLETE**, quá trình này có thể mất vài phút.
{{% /notice %}}

3. Kiểm tra xem **GuardDuty** có được vô hiệu hóa tự động hay không, nếu không thì bạn cần tắt thủ công.
   - Mở **GuardDuty console**.
   - Nhấn vào mục _Settings_ ở menu bên trái.
   - Kéo xuống cuối trang.
   - Nhấn **Disable GuardDuty**.

   ![CleanUp](/images/5/GuardDuty_disable.png?width=90pc)

{{% notice note %}}
Tắt GuardDuty sẽ xoá toàn bộ dữ liệu của dịch vụ này.
{{% /notice %}}

4. Kiểm tra và xoá bất kỳ **EC2 snapshot** nào còn sót lại được tạo trong quá trình workshop.

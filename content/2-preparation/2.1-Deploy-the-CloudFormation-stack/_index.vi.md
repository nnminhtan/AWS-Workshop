+++
title = "Triển khai CloudFormation stack"
date = 2025
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

<!-- ## Triển khai CloudFormation stack -->

Để khởi động kịch bản và tạo cơ sở hạ tầng, chúng ta cần triển khai một mẫu CloudFormation.

{{% notice info %}}
Bạn có thể tải xuống tệp ví dụ tại đây: [Tệp CloudFormation JSON](../../../files/cfn.json).
{{% /notice %}}

1. Truy cập [CloudFormation](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create)

   - Tìm kiếm **CloudFormation**.
   - Chọn **CloudFormation** để mở **CloudFormation Dashboard**.

   ![CloudFormation](../../../images/2/2.1/CloudFormation.png)

2. Trong **CloudFormation Dashboard** 

   - Chọn **Stacks**.
   - Nhấn **Create stack**.

   ![CloudFormation](../../../images/2/2.1/Stack.png?width=90pc)

3. Trong giao diện **Create stack**, tại mục **Create stack**

   - Chọn **Choose an existing template**.
   - Trong phần _Specify template_, chọn **Upload a template file**.
   - Nhấp **Choose file** và tải lên tệp _cfn.json_ đã tải ở bước trên.
   - Nhấn **Next**.

   ![CloudFormation](../../../images/2/2.1/Create_stack.png?width=90pc)

4. Trong giao diện **Specify stack details**

   - Ở mục _Provide a stack name_, nhập tên stack: `AutomatedIncidentResponseWorkshop`.
   - Trong phần _Parameters_, tại _Automatically enable GuardDuty?_ chọn **Yes-Enable GuardDuty**.
   - Giữ nguyên các cài đặt còn lại, nhấn **Next**.

   ![CloudFormation](../../images/2/2.1/Specify_stack_details.png?width=90pc)

5. Trong giao diện **Configure stack options**, tại phần **Capabilities**

   - **Đánh dấu chọn** cả hai ô dưới đây.
     ![CloudFormation](../../images/2/2.1/Capabilities.png?width=90pc)

6. Trong bước **Review and create**:
   - Nếu bạn đã làm các bước trên, hãy cuộn xuống và nhấn nút **Submit**.
   - Trước khi tiếp tục, đảm bảo stack có trạng thái **CREATE_COMPLETE**.

{{% notice note %}}
Quá trình này có thể mất vài phút, bạn có thể tranh thủ đi uống nước trong lúc chờ.
{{% /notice %}}

   ![CloudFormation](../../../images/2/2.1/Stack_create_complete.png?width=90pc)

Nếu trạng thái stack là **CREATE_COMPLETE**, hãy tiếp tục sang bước tiếp theo [Thiết lập Security Group](../2.2-Set-up-Security-Group)

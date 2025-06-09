+++
title = "Triển khai CloudFormation stack"
date = 2025
weight = 1
chapter = false
pre = "<b>3.2.1. </b>"
+++

<!-- #### Tạo IAM Policies & Roles: -->
Để bắt đầu kịch bản và tạo cơ sở hạ tầng cần thiết, chúng ta cần triển khai một CloudFormation template.

{{% notice info %}}
Bạn có thể tải về: [CloudFormation template](/files/IRWorkshop-StepFunctionsResponse.yaml) chứa kiến trúc.
{{% /notice %}}

1. Truy cập vào [CloudFormation](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create)

   - Tìm kiếm **CloudFormation**.
   - Chọn **CloudFormation** để mở **CloudFormation Dashboard**.

   ![CloudFormation](/images/2/2.1/CloudFormation.png)

2. Trong **CloudFormation Dashboard**

   - Chọn **Stacks**.
   - Nhấn **Create stack**.

   ![CloudFormation](/images/2/2.1/Stack.png?width=90pc)

3. Trong giao diện **Create stack**, dưới phần **Create stack**

   - Chọn **Choose an existing template**.
   - Ở mục _Specify template_, chọn **Upload a template file**.
   - Nhấn **Choose file** và tải lên tệp _IRWorkshop-StepFunctionsResponse.yaml_ đã tải ở trên.
   - Nhấn **Next**.

   ![CloudFormation](/images/3/3.2/3.2.1/Create_stack.png?width=90pc)

4. Trong giao diện **Specify stack details**, ở phần **Specify stack details**

   - Ở mục _Provide a stack name_, nhập **Stack name**: `workshop-IR-StepFunctions`.
   - Ở mục _Parameters_, nhập một **địa chỉ email hợp lệ** và một **optional prefix** cho các tài nguyên sẽ được tạo.
   - Nhấn **Next**.

   ![CloudFormation](/images/3/3.2/3.2.1/Specify_stack_details.png?width=90pc)

5. Trong giao diện **Configure stack options**, ở phần **Capabilities**

   - **Chọn dấu tích** vào ô bên dưới.
     ![CloudFormation](/images/3/3.2/3.2.1/Capabilities.png?width=90pc)

6. Trong phần **Review and create**:
   - Nếu bạn làm đúng các bước, hãy cuộn xuống và nhấn nút **Submit**.
   - Trước khi tiếp tục, hãy chắc chắn rằng stack đang ở trạng thái **CREATE_COMPLETE**.

{{% notice note %}}
Quá trình này sẽ mất vài phút, bạn có thể tranh thủ đi uống nước.
{{% /notice %}}

   ![CloudFormation](/images/3/3.2/3.2.1/Stack_create_complete.png?width=90pc)

Nếu stack hiển thị trạng thái **CREATE_COMPLETE**, hãy chuyển sang bước tiếp theo [Đăng ký SNS](../3.2.2-SNS-subscription)

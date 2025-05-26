+++
title = "Gắn policy vào role"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

## Gắn policy vào role

Ở phần này, ta gắn policy vào role đã tạo trước, để đảm bảo role có các quyền tương ứng được định nghĩa trong policy

1. Trong IAM Dashboard

   - Chọn **Role**
   - Chọn vào role **AWSGlueServiceRoleDefault**

   ![IAM](/images/1/1.3/choose_role_ud.png?width=90pc)

2. Trong chi tiết role **AWSGlueServiceRoleDefault**, chọn **Attach policy**

   ![IAM](/images/1/1.3/click_attach_ud.png?width=90pc)

3. Chọn **AWSGlueServicePolicy**, click **Add permission**

   ![IAM](/images/1/1.3/add_permisstion_policy_ud.png?width=90pc)

4. Attach policy vào role thành công

   ![IAM](/images/1/1.3/attach_success_ud.png?width=90pc)

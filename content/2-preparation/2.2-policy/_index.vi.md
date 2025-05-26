+++
title = "Tạo policy"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

## Tạo policy

Tiếp theo, ta sẽ tạo 1 policy.

1. Tại giao diện **IAM**

   - Chọn **Policy**
   - Chọn **Create policy**

   ![Policy](/images/1/create_policy.png)

2. Tại giao diện **Create policy**, ở bước **Specify permission**

   - Chọn **JSON**
   - Paste đoạn code sau vào **Policy Editor**, chú ý để **AccountID** là account ID của bạn.
   - Sau đó chọn **Next**

```
    {
     "Version": "2012-10-17",
     "Statement": [
            {
                "Effect": "Allow",
                "Action": "iam:PassRole",
                "Resource": "arn:aws:iam::AccountID:role/AWSGlueServiceRoleDefault"
            }
        ]
    }
```

![Policy](/images/1/policy_permission.png)

3. Tại giao diện **Create policy**, ở bước **Review and create**

   - Đặt **Policy name** là `AWSGlueServicePolicy`

   ![Policy](/images/1/name_policy.png)

   - Review lại các thông số và chọn **Create policy**

   ![Policy](/images/1/create_policy_submit.png)

4. Tạo policy thành công
   ![Policy](/images/1/policy_success.png)

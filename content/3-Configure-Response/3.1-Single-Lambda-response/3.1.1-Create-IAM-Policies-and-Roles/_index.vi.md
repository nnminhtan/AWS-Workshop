+++
title = "Dọn dẹp tài nguyên"
date = 2025
weight = 1
chapter = false
pre = "<b>3.1.1. </b>"
+++

<!-- #### Tạo IAM Policies & Roles: -->
Vì bạn đang ở IAM dashboard từ bước trước, bây giờ hãy chuyển sang phần Policies để tạo một policy cho _execution role_.

1. Tạo policy cho **execution role**

   - Đầu tiên nhấn **Create policy**

    ![Lambda](../../../../images/3/3.1/3.1.1/Create_policy.png?width=90pc)

   - Chọn định dạng **json** và dán đoạn JSON sau vào **Policy editor**, sau đó nhấn _Next_

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "EC2Snapshot",
                "Effect": "Allow",
                "Action": [
                    "ec2:AuthorizeSecurityGroupIngress",
                    "ec2:Describe*",
                    "logs:CreateLogStream",
                    "ec2:CreateSecurityGroup",
                    "ec2:CreateTags",
                    "ec2:CreateSnapshots",
                    "ec2:CreateSnapshot",
                    "ec2:ModifyInstanceAttribute",
                    "ec2:StopInstances",
                    "logs:CreateLogGroup",
                    "logs:PutLogEvents"
                ],
                "Resource": "*"
            }
        ]
    }
    ```
   - Kết quả sẽ như hình dưới đây.

    ![Lambda](../../../../images/3/3.1/3.1.1/Create_policy_add_permission.png?width=90pc)

   - Đặt tên cho policy là: `ec2instance-containment-with-forensics-policy` và giữ nguyên các thiết lập còn lại, sau đó nhấn _Create policy_.

    ![Lambda](../../../../images/3/3.1/3.1.1/Create_policy_naming.png?width=90pc)

2. Tạo _execution role_ cho **Lambda Function**

   - Vẫn trong **IAM dashboard**, chuyển sang phần Roles ở thanh bên trái, chọn **Create role**

    ![Lambda](../../../../images/3/3.1/3.1.1/Create_role.png?width=90pc)

   - Mặc định _Trusted entity type_ sẽ là **AWS service**.
   - Ở phần _Service or use case_, chọn **Lambda** rồi nhấn _Next_.

    ![Lambda](../../../../images/3/3.1/3.1.1/Create_role_use_case.png?width=90pc)

   - Gán policy `ec2instance-containment-with-forensics-policy` vừa tạo và nhấn Next.

    ![Lambda](../../../../images/3/3.1/3.1.1/Create_role_add_permission.png?width=90pc)

   - Đặt tên Role là `ec2instance-containment-with-forensics-role`, giữ nguyên các thiết lập còn lại và nhấn _Create Role_.

    ![Lambda](../../../../images/3/3.1/3.1.1/Create_role_naming.png?width=90pc)

Sau khi hoàn tất, bạn có thể chuyển sang bước tiếp theo [Create Lambda Function](../3.1.2-Create-Lambda-Function)

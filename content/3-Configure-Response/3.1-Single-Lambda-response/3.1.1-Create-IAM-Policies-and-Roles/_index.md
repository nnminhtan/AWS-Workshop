+++
title = "Create IAM Policies and Roles"
date = 2025
weight = 1
chapter = false
pre = "<b>3.1.1. </b>"
+++


<!-- #### Create IAM Policies & Roles: -->
Since you are already at the IAM dashboard for the last step, now headed to the policies and create one for the _execution role_ 

1. Create a policy for the **execution role**
   - First click **Create policy**

    ![Lambda](/images/3/3.1/3.1.1/Create_policy.png?width=90pc)

   - Click the **json** format and paste the following into the **Policy editor** and click _Next_

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
    - The result should be like this.
    
    ![Lambda](/images/3/3.1/3.1.1/Create_policy_add_permission.png?width=90pc)

    - **Name** the policy : `ec2instance-containment-with-forensics-policy` and leave the rest unchanged, then _Create policy_.

    ![Lambda](/images/3/3.1/3.1.1/Create_policy_naming.png?width=90pc)

2. Create the _execution role_ for the **Lambda Function**
   - Still in the **IAM dashboard**, head to the roles in the left side panel, Select **Create role** 

    ![Lambda](/images/3/3.1/3.1.1/Create_role.png?width=90pc)
    
   - The default _Trusted entity type_ should be **AWS service**. 
   - Under _Service or use case_, Select **Lambda** and click _Next_.

    ![Lambda](/images/3/3.1/3.1.1/Create_role_use_case.png?width=90pc)

   - Add the prior created `ec2instance-containment-with-forensics-policy` policy and click next.

    ![Lambda](/images/3/3.1/3.1.1/Create_role_add_permission.png?width=90pc)

   - Name the Role `ec2instance-containment-with-forensics-role` and leave every unchanged, click _Create Role_.

    ![Lambda](/images/3/3.1/3.1.1/Create_role_naming.png?width=90pc)

If you done with that go to the next step which is [Create Lambda Function](../3.1.2-Create-Lambda-Function)



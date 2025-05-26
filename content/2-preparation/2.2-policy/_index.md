+++
title = "Create Policy"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

## Creating a Policy

Next, we will create a policy.

1. In the **IAM** interface

   - Select **Policies**
   - Click **Create policy**

   ![Policy](/images/1/create_policy.png)

2. In the **Create policy** interface, under **Specify permission**

   - Select **JSON**
   - Paste the following code into the **Policy Editor**, replacing **AccountID** with your actual AWS account ID.
   - Click **Next**

```json
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

3. In the **Create policy** interface, under **Review and create**

   - Set **Policy name** to `AWSGlueServicePolicy`

   ![Policy](/images/1/name_policy.png)

   - Review the settings and click **Create policy**

   ![Policy](/images/1/create_policy_submit.png)

4. Policy created successfully:
   ![Policy](/images/1/policy_success.png)

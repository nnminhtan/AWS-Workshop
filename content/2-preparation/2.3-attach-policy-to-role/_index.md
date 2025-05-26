+++
title = "Attach Policy to Role"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

## Attach Policy to Role

In this section, we attach the policy to the previously created role to ensure the role has the appropriate permissions defined in the policy.

1. In the **IAM Dashboard**

   - Select **Role**
   - Click on the role **AWSGlueServiceRoleDefault**

   ![IAM](/images/1/1.3/choose_role_ud.png?width=90pc)

2. In the **AWSGlueServiceRoleDefault** role details, select **Attach policy**

   ![IAM](/images/1/1.3/click_attach_ud.png?width=90pc)

3. Select **AWSGlueServicePolicy**, then click **Add permission**

   ![IAM](/images/1/1.3/add_permisstion_policy_ud.png?width=90pc)

4. Policy successfully attached to the role

   ![IAM](/images/1/1.3/attach_success_ud.png?width=90pc)

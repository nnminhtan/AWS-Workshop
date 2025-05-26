+++
title = "Create IAM Role"
date = 2024
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

## Creating an IAM Role

In this step, we will navigate to the IAM Console and create a role for the Glue service. This role will allow AWS Glue to access data stored in S3 and create necessary objects in the Glue Catalog.

1. Access the [AWS Management Console](https://aws.amazon.com/console/)

   - Search for **IAM**
   - Select **IAM** to open the **IAM Dashboard**

   ![IAM](/images/1/iam-service-cropped.png)

2. In the IAM Dashboard

   - Select **Roles**
   - Click **Create role**

   ![IAM](/images/1/create_iam_role_cropped.png?width=90pc)

3. In the **Create role** interface, under **Select trusted entity**

   - Choose **AWS Service**
   - Under _Service or use case_, select **Glue**
   - Click **Next**

   ![IAM](/images/1/create_iam_role_detail.png?width=90pc)

4. In the **Create role** interface, under **Add Permission**

   - Search for and select **AmazonS3FullAccess**

   ![AmazonS3FullAccess](/images/1/add_s3_permission_2step.png?width=90pc)

   - Search for and select **AWSGlueServiceRole**
   - Click **Next**

   ![AWSGlueServiceRole](/images/1/add_glue_permission.png?width=90pc)

5. In the **Create role** interface, under **Name, review and create**

   - In **Role name**, enter `AWSGlueServiceRoleDefault`
     ![AWSGlueServiceRole](/images/1/name_role.png?width=90pc)
   - Review the role details under **Select trusted entity** and **Add Permission**
     ![AWSGlueServiceRole](/images/1/review_role.png?width=90pc)
   - Click **Create role**
     ![AWSGlueServiceRole](/images/1/create_role_submit.png?width=90pc)

6. Successful role creation interface:
   ![AWSGlueServiceRole](/images/1/create_role_success.png?width=90pc)

+++
title = "Tạo IAM role"
date = 2024
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

## Tạo IAM Role

Trong bước này, chúng ta sẽ chuyển tới giao diện IAM Console và tạo role cho dịch vụ Glue. Role này sẽ cho phép AWS Glue truy cập tới dữ liệu nằm trong S3 và tạo các đối tượng cần thiết trong Glue Catalog.

1. Truy cập vào giao diện [AWS Management Console](https://aws.amazon.com/console/)

   - Tìm **IAM**
   - Chọn **IAM** để vào **IAM Dashboard**

   ![IAM](/images/1/iam-service-cropped.png)

2. Trong IAM Dashboard

   - Chọn **Role**
   - Chọn **Create role**

   ![IAM](/images/1/create_iam_role_cropped.png?width=90pc)

3. Trong giao diện **Create role**, ở bước **Select trusted entity**

   - Chọn **AWS Service**
   - Ở phần _Service or use case_ chọn **Glue**
   - Chọn **Next**

   ![IAM](/images/1/create_iam_role_detail.png?width=90pc)

4. Trong giao diện **Create role**, ở bước **Add Permission**

   - Tìm và chọn **AmazonS3FullAccess**

   ![AmazonS3FullAccess](/images/1/add_s3_permission_2step.png?width=90pc)

   - Tìm và chọn **AWSGlueServiceRole**
   - Chọn **Next**

   ![AWSGlueServiceRole](/images/1/add_glue_permission.png?width=90pc)

5. Trong giao diện **Create role**, ở bước **Name, review and create**

   - Ở **Role name**, đặt tên `AWSGlueServiceRoleDefault`
     ![AWSGlueServiceRole](/images/1/name_role.png?width=90pc)
   - Xem lại thông tin role tại **Select trusted entity** và **Add Permission**
     ![AWSGlueServiceRole](/images/1/review_role.png?width=90pc)
   - Chọn **Create role**
     ![AWSGlueServiceRole](/images/1/create_role_submit.png?width=90pc)

6. Giao diện tạo role thành công:
   ![AWSGlueServiceRole](/images/1/create_role_success.png?width=90pc)

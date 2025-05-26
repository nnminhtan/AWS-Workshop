+++
title = "Dọn dẹp tài nguyên"
date = 2021-06-08T18:57:03+07:00
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

Chúng ta sẽ dọn dẹp các tài nguyên sau:

#### **Dọn dẹp tài nguyên ở Visual QuickSight**:

1.  **Xóa Pie chart sheet**

![QuickSight](/images/7/delete_piechart.png?width=90pc)

2. **Xóa Analyses QuickSight:**

- Chọn **Analyses**.
- Chọn **Analysis** cần xóa.
- Chọn **Delete**.

![QuickSight](/images/7/delete_qs_ana.png?width=90pc)

- Delete done

![QuickSight](/images/7/delete_done.png?width=90pc)

3. **Xóa Dataset QuickSight:**

![QuickSight](/images/7/delete_dataset.png?width=90pc)
![QuickSight](/images/7/delete_cf_dataset.png?width=90pc)

4. Bạn cũng có thể xóa tài khoản QuickSight nếu không sử dụng

- Tại giao diện **QuickSight**, chọn **Manage QuickSight**

![QuickSight](/images/6/6.2/manage_quicksight.png?width=90pc)

- Tại **Account settings**, chọn **Manage**

![QuickSight](/images/7/delete_qs_acc.png?width=90pc)

- Thực hiện xóa tài khoản

![QuickSight](/images/7/delete_acc_form.png?width=90pc)

- Hủy đăng ký **QuickSight** thành công

![QuickSight](/images/7/delete_success.png?width=90pc)

---

#### **Dọn dẹp tài nguyên ở AWS Glue**:

Truy cập vào **AWS Glue**.

1. **Xóa các tables**

- Chọn **Tables**.
- Chọn các table cần xóa.
- Chọn **Delete** để xác nhận xóa Table.

![QuickSight](/images/7/delete_tables.png?width=90pc)
![QuickSight](/images/7/cf_delete_table.png?width=90pc)

2. **Xóa Interactive Sessions**

- Chọn **Interactive Sessions**.
- Chọn các session cần xóa.
- Chọn **Delete** để xác nhận xóa session.

![QuickSight](/images/7/delete_session.png?width=90pc)

2. **Xóa crawler**

- Chọn **Crawler**.
- Chọn các crawler cần xóa.
- Chọn Action
- Chọn **Delete crawler** để xác nhận xóa crawler.

![QuickSight](/images/7/delete_cwl.png?width=90pc)

---

#### **Dọn dẹp tài nguyên ở CloudFormation**:

- Vào giao diện **CloudFormation**
- Chọn **Stack**
- Chọn **stack name** cần xóa
- Chọn **Delete**

![QuickSight](/images/7/delete_cloudform.png?width=90pc)

- Nếu delete stack **fail**
  - Chọn **Retry delete**
  - Chọn **Force delete this entire stack**

![QuickSight](/images/7/force_delete_stack.png?width=90pc)

---

#### **Dọn dẹp tài nguyên ở Kinesis**:

- Vào **Amazon Data Firehose**
- Chọn **Firehose stream** cần xóa
- Chọn **Delete**

![QuickSight](/images/7/delete_firehose.png?width=90pc)
![QuickSight](/images/7/cf_delete_firehose.png?width=90pc)

---

#### **Dọn dẹp tài nguyên ở CloudWatch**:

- Vào giao diện **CloudWatch**
- Chọn **Log groups**
- Chọn tất cả **Log groups**
- Chọn **Action**
- Chọn **Delete log group(s)**

![QuickSight](/images/7/delete_logs.png?width=90pc)
![QuickSight](/images/7/cf_delete_logs.png?width=90pc)

---

#### **Dọn dẹp tài nguyên ở S3**:

- Xóa tất cả các bucket liên quan tới bài lab

- Chọn **bucket**
- **Empty bucket**

![QuickSight](/images/7/empty__bucket.png?width=90pc)
![QuickSight](/images/7/cf_empty_s3.png?width=90pc)

- Chọn lại bucket vừa empty
- Chọn **Delete**

![QuickSight](/images/7/delete_s3_bucket.png?width=90pc)
![QuickSight](/images/7/cf_delete_bucket.png?width=90pc)

{{% notice note %}}
Thực hiện tương tự với các bucket còn lại
{{% /notice %}}

---

#### **Dọn dẹp tài nguyên ở IAM**:

Vào giao diện IAM

**1. Xóa Policy**

- Chọn **Policies**
- Chọn **policy** liên quan đến bài lab
- Chọn **Delete**

![QuickSight](/images/7/delete_policy.png?width=90pc)
![QuickSight](/images/7/cf_delete_policy.png?width=90pc)

- Xóa policy thành công

![QuickSight](/images/7/delete_policy_success.png?width=90pc)

**2. Xóa Role**

- Chọn **Roles**
- Chọn **role** liên quan đến bài lab
- Chọn **Delete**

![QuickSight](/images/7/delete_role.png?width=90pc)

- Xóa role thành công

![QuickSight](/images/7/delete_role_success.png?width=90pc)

+++
title = "Cleanup Resources"
date = 2021-06-08T18:57:03+07:00
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

We will clean up the following resources:

#### **Clean up resources in Visual QuickSight**:

1.  **Delete Pie Chart Sheet**

![QuickSight](/images/7/delete_piechart.png?width=90pc)

2. **Delete QuickSight Analyses:**

- Select **Analyses**.
- Select the **Analysis** you want to delete.
- Click **Delete**.

![QuickSight](/images/7/delete_qs_ana.png?width=90pc)

- Delete done

![QuickSight](/images/7/delete_done.png?width=90pc)

3. **Delete QuickSight Dataset:**

![QuickSight](/images/7/delete_dataset.png?width=90pc)
![QuickSight](/images/7/delete_cf_dataset.png?width=90pc)

4. You can also delete your QuickSight account if not using it.

- In the **QuickSight** interface, click **Manage QuickSight**

![QuickSight](/images/6/6.2/manage_quicksight.png?width=90pc)

- Under **Account settings**, click **Manage**

![QuickSight](/images/7/delete_qs_acc.png?width=90pc)

- Proceed to delete the account

![QuickSight](/images/7/delete_acc_form.png?width=90pc)

- QuickSight unsubscription successful

![QuickSight](/images/7/delete_success.png?width=90pc)

---

#### **Clean up resources in AWS Glue**:

Access **AWS Glue**.

1. **Delete Tables**

- Select **Tables**.
- Choose the tables to delete.
- Click **Delete** to confirm table deletion.

![QuickSight](/images/7/delete_tables.png?width=90pc)
![QuickSight](/images/7/cf_delete_table.png?width=90pc)

2. **Delete Interactive Sessions**

- Select **Interactive Sessions**.
- Choose the sessions to delete.
- Click **Delete** to confirm session deletion.

![QuickSight](/images/7/delete_session.png?width=90pc)

3. **Delete Crawlers**

- Select **Crawler**.
- Choose the crawlers to delete.
- Click **Action**
- Select **Delete crawler** to confirm crawler deletion.

![QuickSight](/images/7/delete_cwl.png?width=90pc)

---

#### **Clean up resources in CloudFormation**:

- Go to the **CloudFormation** interface.
- Select **Stack**
- Choose the **stack name** you want to delete.
- Click **Delete**

![QuickSight](/images/7/delete_cloudform.png?width=90pc)

- If the stack deletion **fails**
  - Click **Retry delete**
  - Click **Force delete this entire stack**

![QuickSight](/images/7/force_delete_stack.png?width=90pc)

---

#### **Clean up resources in Kinesis**:

- Go to **Amazon Data Firehose**
- Select the **Firehose stream** to delete.
- Click **Delete**

![QuickSight](/images/7/delete_firehose.png?width=90pc)
![QuickSight](/images/7/cf_delete_firehose.png?width=90pc)

---

#### **Clean up resources in CloudWatch**:

- Go to the **CloudWatch** interface.
- Select **Log groups**
- Select all **Log groups**
- Click **Action**
- Select **Delete log group(s)**

![QuickSight](/images/7/delete_logs.png?width=90pc)
![QuickSight](/images/7/cf_delete_logs.png?width=90pc)

---

#### **Clean up resources in S3**:

- Delete all buckets related to the lab

- Select **bucket**
- Click **Empty bucket**

![QuickSight](/images/7/empty__bucket.png?width=90pc)
![QuickSight](/images/7/cf_empty_s3.png?width=90pc)

- Select the emptied bucket
- Click **Delete**

![QuickSight](/images/7/delete_s3_bucket.png?width=90pc)
![QuickSight](/images/7/cf_delete_bucket.png?width=90pc)

{{% notice note %}}
Perform the same action for the remaining buckets
{{% /notice %}}

---

#### **Clean up resources in IAM**:

Go to the IAM interface

**1. Delete Policy**

- Select **Policies**
- Choose the **policy** related to the lab
- Click **Delete**

![QuickSight](/images/7/delete_policy.png?width=90pc)
![QuickSight](/images/7/cf_delete_policy.png?width=90pc)

- Policy deleted successfully

![QuickSight](/images/7/delete_policy_success.png?width=90pc)

**2. Delete Role**

- Select **Roles**
- Choose the **role** related to the lab
- Click **Delete**

![QuickSight](/images/7/delete_role.png?width=90pc)

- Role deleted successfully

![QuickSight](/images/7/delete_role_success.png?width=90pc)

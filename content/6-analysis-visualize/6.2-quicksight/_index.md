+++
title = "Visualize with QuickSight"
date = 2020
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++

## Visualize with QuickSight

We will use **QuickSight** to visualize data from the **processed_data** table.

First, we will create a **QuickSight** account.

{{% notice info %}}
If you already have a **QuickSight** account, you can skip this step.
{{% /notice %}}

### Create a QuickSight Account

1. Search for and select the **QuickSight** service

![QuickSight](/images/6/6.2/quicksight.png?width=90pc)

2. Sign up for **QuickSight**

![QuickSight](/images/6/6.2/signup_ud.png?width=90pc)

3. Enter your **email**, select **Authentication Method**, and choose the region **Asia Pacific (Singapore)**

![QuickSight](/images/6/6.2/quicksight_form_ud.png?width=90pc)

4. In **Account info**:

- Enter `demo-visualize` as the **QuickSight account name**
- IAM role: select **Use QuickSight-managed role (default)**

![QuickSight](/images/6/6.2/quicksight_form2.png?width=90pc)

- Select **Finish**

![QuickSight](/images/6/6.2/fiinish_signup.png?width=90pc)

- After successfully signing up, you will be redirected to the **QuickSight** dashboard.

![QuickSight](/images/6/6.2/quicksight_dashboard.png?width=90pc)

### Visualize Data

1. On the **QuickSight** dashboard, select **Manage QuickSight**

![QuickSight](/images/6/6.2/manage_quicksight.png?width=90pc)

2. Select **Security & permissions**, then select **Manage**

![QuickSight](/images/6/6.2/click_manage_setting.png?width=90pc)

3. Check the services

- For **Amazon S3**: select **S3 Buckets Linked To QuickSight Account**, choose the bucket **asg-datalake-demo-2024**, and then select **Finish**

![QuickSight](/images/6/6.2/allow_s3.png?width=90pc)

4. Check the other services and then select **Save**

![QuickSight](/images/6/6.2/save_allow.png?width=90pc)

5. Return to the **QuickSight** dashboard

- Select **Dataset**
- Select **New dataset**

![QuickSight](/images/6/6.2/create_dataset_btn_ud.png?width=90pc)

6. Create a **data source**

- Select **Athena**
- Enter **Data source name** as `summitdemo`
- Select **Validate Connection**. If the connection is successful, it will display **SSL is enabled**
- Select **Create data source**

![QuickSight](/images/6/6.2/create_data_source.png?width=90pc)

7. Select **Table**:

- **Catalog**, select **AwsDataCatalog**
- **Database**, enter `summitdb`
- **Table**, select **processed_data**
- Select **Select**

![QuickSight](/images/6/6.2/select_table.png?width=90pc)

8. In the **Finish dataset creation** step:

- Select **Directly query your data**
- Select **Visualize**

![QuickSight](/images/6/6.2/finish_create_dataset.png?width=90pc)

9. Use **Amazon QuickSight** to visualize the transformed data:

- Create a **Tree map** of users and the number of tracks they listened to.
- Click to select **Tree Map**

![QuickSight](/images/6/6.2/tree_map.png?width=90pc)

- Result of the **Tree map**

![QuickSight](/images/6/6.2/treemap.png?width=90pc)

10. You can also use other **Visual types**, such as **Pie chart**

![QuickSight](/images/6/6.2/piechart.png?width=90pc)

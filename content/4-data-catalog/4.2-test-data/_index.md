+++
title = "Check Data"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

## Check Data

1. Search and select the **S3** service

![S3](/images/3/s3.png?width=90pc)

2. Select the bucket **asg-datalake-demo-2024**

![S3](/images/4/4.2/choose_bucket.png?width=90pc)

3. Click **Create folder**

![S3](/images/4/4.2/create_fd_btn.png?width=90pc)

4. Name the folder **Athena**, then click **Create folder**

![S3](/images/4/4.2/name_create.png?width=90pc)

5. The result is as follows:

![S3](/images/4/4.2/result_fd.png?width=90pc)

Next, we will use **Athena** with SQL queries to check the data structure.

6. Search and select the **Athena** service

![S3](/images/4/4.2/athena.png?width=90pc)

7. In the **Query editor**, click **Settings**, then select **Manage**

![S3](/images/4/4.2/manage_Athena.png?width=90pc)

8. In the **Manage settings**

- Click **Browse S3**
- Select the path to the **Athena** folder
- Click **Save**

![S3](/images/4/4.2/set_path_athena.png?width=90pc)

9. Run a query with:

- **Data source**: **AwsDataCatalog**
- **Database**: **summitdb**
- Run the query: retrieve 10 rows from the table raw2024

```
SELECT * FROM "summitdb"."raw2024" limit 10
```

- Click **Run** query

10. The result of the query is:

![S3](/images/4/4.2/query1_result.png?width=90pc)

9. Continue running a query with:

- **Data source**: **AwsDataCatalog**
- **Database**: **summitdb**
- Run the query:

```
SELECT activity_type,
       count(activity_type)
FROM raw2024
GROUP BY activity_type
ORDER BY activity_type

```

- Click **Run** query

10. The result of the query is:

![S3](/images/4/4.2/query1_result.png?width=90pc)

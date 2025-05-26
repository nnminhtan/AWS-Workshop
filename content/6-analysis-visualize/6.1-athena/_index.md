+++
title = "Analysis with Athena"
date = 2020
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

## Analysis with Athena

1. Search for and select the **Athena** service

![S3](/images/4/4.2/athena.png?width=90pc)

2. Execute the query with:

- **Data source**: **AwsDataCatalog**
- **Database**: **summitdb**
- Execute the query:

```
SELECT artist_name,
       count(artist_name) AS count
FROM processed_data
GROUP BY artist_name
ORDER BY count DESC

```

![S3](/images/6/6.1/query_athena.png?width=90pc)

- Select **Run** query

3. The result of the above query:

![S3](/images/6/6.1/result_query1.png?width=90pc)

4. Next, execute the following query:

```
SELECT device_id,
       track_name,
       count(track_name) AS count
FROM processed_data
GROUP BY device_id, track_name
ORDER BY count DESC


```

![S3](/images/6/6.1/query2.png?width=90pc)

- Select **Run** query

5. The result of the above query:

![S3](/images/6/6.1/result_query2.png?width=90pc)

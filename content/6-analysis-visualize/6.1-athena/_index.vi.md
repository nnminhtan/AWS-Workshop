+++
title = "Phân tích với Athena"
date = 2020
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

## Phân tích với Athena

1. Tìm kiếm và chọn dịch vụ **Athena**

![S3](/images/4/4.2/athena.png?width=90pc)

2. Thực hiện query với:

- **Data source**: **AwsDataCatalog**
- **Database**: **summitdb**
- Thực hiện câu truy vấn:

```
SELECT artist_name,
       count(artist_name) AS count
FROM processed_data
GROUP BY artist_name
ORDER BY count DESC

```

![S3](/images/6/6.1/query_athena.png?width=90pc)

- Chọn **Run** query

3. Kết quả câu truy vấn trên:

![S3](/images/6/6.1/result_query1.png?width=90pc)

2. Tiếp theo, thực hiện query với:

```
SELECT device_id,
       track_name,
       count(track_name) AS count
FROM processed_data
GROUP BY device_id, track_name
ORDER BY count DESC


```

![S3](/images/6/6.1/query2.png?width=90pc)

- Chọn **Run** query

3. Kết quả câu truy vấn trên:

![S3](/images/6/6.1/result_query2.png?width=90pc)

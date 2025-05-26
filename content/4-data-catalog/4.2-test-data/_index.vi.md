+++
title = "Kiểm tra dữ liệu"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

## Kiểm tra dữ liệu

1. Tìm kiếm và chọn dịch vụ **S3**

![S3](/images/3/s3.png?width=90pc)

2. Chọn vào bucket **asg-datalake-demo-2024**

![S3](/images/4/4.2/choose_bucket.png?width=90pc)

3. Chọn **Create folder**

![S3](/images/4/4.2/create_fd_btn.png?width=90pc)

4. Đặt tên cho folder là **Athena**, sau đó chọn **Create folder**

![S3](/images/4/4.2/name_create.png?width=90pc)

5. Ta được kết quả

![S3](/images/4/4.2/result_fd.png?width=90pc)

Tiếp theo, ta sẽ sử dụng **Athena** cùng các câu truy vấn để kiểm tra cấu trúc dữ liệu

6. Tìm kiếm và chọn dịch vụ **Athena**

![S3](/images/4/4.2/athena.png?width=90pc)

7. Trong **Query editor**, chọn **Settings**, sau đó chọn **Manage**

![S3](/images/4/4.2/manage_Athena.png?width=90pc)

8. Trong **Manage settings**

- Chọn **Browse S3**
- Chọn đường dẫn dẫn tới thư mục **Athena**
- Chọn **Save**

![S3](/images/4/4.2/set_path_athena.png?width=90pc)

9. Thực hiện query với:

- **Data source**: **AwsDataCatalog**
- **Database**: **summitdb**
- Thực hiện câu truy vấn: lấy 10 dòng của table raw2024

```
SELECT * FROM "summitdb"."raw2024" limit 10
```

- Chọn **Run** query

10. Kết quả câu truy vấn trên:

![S3](/images/4/4.2/query1_result.png?width=90pc)

9. Tiếp tục thực hiện query với:

- **Data source**: **AwsDataCatalog**
- **Database**: **summitdb**
- Thực hiện câu truy vấn:

```
SELECT activity_type,
       count(activity_type)
FROM raw2024
GROUP BY activity_type
ORDER BY activity_type

```

- Chọn **Run** query

10. Kết quả câu truy vấn trên:

![S3](/images/4/4.2/query1_result.png?width=90pc)

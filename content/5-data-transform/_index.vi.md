+++
title = "Chuyển đổi dữ liệu"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

### Chuyển đổi dữ liệu

1. Tìm kiếm và chọn dịch vụ **Glue**

![Glue](/images/5/glue.png?width=90pc)

2. Chọn **Notebook**

![Glue](/images/5/create_notebook_btn.png?width=90pc)

3. Tải file [notebook.ipynb](https://github.com/ngcuyen/ws-doc/blob/main/notebook.ipynb)

4. Ở form **Notebook**

- Chọn **Upload Notebook**
- Chọn **Choose file**
- Chọn file notebook đã tải
- IAM role: chọn **AWSGlueServiceRoleDefault**
- Chọn **Create notebook**

![Glue](/images/5/upload_notebook.png?width=90pc)

5. Đợi **notebook** start, ta chạy từng **cell** notebook và xem kết quả

- Đầu tiên, chúng ta sẽ run cell để tạo session

![Glue](/images/5/nb1.png?width=90pc)

- Khởi tạo session thành công

![Glue](/images/5/nb1.1.png?width=90pc)

- Vào **Interactive Session**, kiểm tra thấy session đã được tạo thành công

![Glue](/images/5/session_created.png?width=90pc)

- Ở cell [2]: Import các libraries **SparkContext, GlueContext, boto3, awsglue và khởi tạo session**
- Ở cell [3]: Câu lệnh khởi tạo **GlueContext** để sử dụng các tính năng **ETL** của **AWS Glue** và lấy **SparkSession** để xử lý dữ liệu bằng **Apache Spark**.

![Glue](/images/5/nb23.png?width=90pc)

- Ở cell [4]: tạo hai **DynamicFrames** **raw_data** và **reference_data** bằng cách truy xuất dữ liệu từ các bảng **raw2024** và **reference_data** trong cơ sở dữ liệu **summitdb** trong **AWS Glue Data Catalog**.
- Ở cell [5]: Câu lệnh raw_data.printSchema() hiển thị cấu trúc lược đồ (schema) của **DynamicFrame** **raw_data**, bao gồm các cột, kiểu dữ liệu và cấu trúc lồng nhau (nếu có).

![Glue](/images/5/nb45.png?width=90pc)

- Ở cell [6]: Câu lệnh reference_data.printSchema() hiển thị cấu trúc lược đồ (schema) của **DynamicFrame** **reference_data**, bao gồm các cột và kiểu dữ liệu tương ứng.
- Ở cell [7]: Các câu lệnh này sẽ in ra số lượng bản ghi của hai **DynamicFrames** **raw_data** và **reference_data**.

![Glue](/images/5/nb67.png?width=90pc)

- Ở cell [8]: xem nhanh 5 bản ghi đầu tiên trong raw_data dưới dạng **DataFrame Spark**.

![Glue](/images/5/nb8.png?width=90pc)

- Ở cell [9]: xem nhanh 5 bản ghi đầu tiên trong reference_data dưới dạng **DataFrame Spark**.

![Glue](/images/5/nb9.png?width=90pc)

- Ở cell [10]: tạo một bảng tạm thời từ **raw_data**, truy vấn các bản ghi có **activity_type** là "**Running**" và hiển thị số lượng cũng như 5 dòng đầu tiên của kết quả.

![Glue](/images/5/nb10.png?width=90pc)

- Ở cell [11]: truy vấn các bản ghi có **activity_type** là "**Working**" từ bảng tạm thời **temp_raw_data**, hiển thị số lượng kết quả và 5 dòng đầu tiên của chúng.

![Glue](/images/5/nb11.png?width=90pc)

- Ở cell [12]: áp dụng một hàm lọc để chỉ giữ lại các bản ghi có **activity_type** là "**Running**" từ **raw_data** và sau đó đếm số lượng bản ghi này.

![Glue](/images/5/nb12.png?width=90pc)

- Ở cell [13]: giữ lại các bản ghi có **activity_type** là "**Working**" từ **raw_data** và sau đó in ra số lượng bản ghi này.
- Ở cell [14]: thực hiện phép nối giữa **raw_data** và **reference_data** dựa trên trường **track_id**, tạo ra một **DynamicFrame** mới có tên là **joined_data**

![Glue](/images/5/nb1314.png?width=90pc)

- Ở cell [15]: cho cái nhìn tổng quan về các trường và kiểu dữ liệu sau khi hai **DynamicFrame** được nối lại với nhau.

![Glue](/images/5/nb15.png?width=90pc)

- Ở cell [16]: loại bỏ các trường không cần thiết (**partition_0, partition_1, partition_2, partition_3**) khỏi **joined_data** và lưu kết quả vào **joined_data_clean**

![Glue](/images/5/nb16.png?width=90pc)

- Ở cell [17]: hiển thị lược đồ của **joined_data_clean** sau khi đã làm sạch dữ liệu bằng cách loại bỏ các trường không mong muốn

![Glue](/images/5/nb17.png?width=90pc)

- Ở cell [18]: xem nhanh 5 bản ghi đầu tiên trong **joined_data_clean** dưới dạng **DataFrame Spark**.

![Glue](/images/5/nb18.png?width=90pc)

- Ở cell [19]: ghi dữ liệu từ **joined_data_clean** vào S3 trong định dạng Parquet, và nếu có lỗi xảy ra trong quá trình ghi, thông báo lỗi sẽ được in ra.

![Glue](/images/5/nb19.png?width=90pc)

- Ở cell [20]: sử dụng **Boto3** để khởi chạy **summitcrawler**, sau đó kiểm tra trạng thái của crawler trong một vòng lặp cho đến khi crawler dừng lại. Khi crawler dừng, chương trình in ra thông báo và kết thúc.

![Glue](/images/5/nb20.png?width=90pc)

- Ở cell [21]: sử dụng **AWS Glue client** để lấy danh sách các bảng trong cơ sở dữ liệu **summitdb** và in ra tên của từng bảng.

![Glue](/images/5/nb21.png?width=90pc)

6. Kiểm tra dữ liệu đã được nạp vào **S3** hay chưa, tìm kiếm và chọn dịch vụ **S3**

![S3](/images/3/s3.png?width=90pc)

7. Kiểm tra tại **asg-datalake-demo-2024/data**

![S3](/images/5/processdata_ins3.png?width=90pc)

8. Kiểm tra các object có trong **processed-data**

![S3](/images/5/object_in_processdata.png?width=90pc)

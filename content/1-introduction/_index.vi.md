+++
title = "Giới thiệu"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

# Tìm hiểu về Data Lake trên AWS

#### Giới thiệu Data Lake

**Data Lake** là một hệ thống lưu trữ tập trung cho phép lưu trữ dữ liệu dưới mọi định dạng - có cấu trúc, bán cấu trúc hoặc không cấu trúc. Không giống như các cơ sở dữ liệu truyền thống yêu cầu định dạng dữ liệu trước khi lưu trữ, Data Lake cho phép lưu trữ dữ liệu thô và xử lý hoặc phân tích khi cần.

#### Lợi ích của Data Lake

- **Lưu trữ linh hoạt**: Hỗ trợ dữ liệu từ nhiều nguồn và dưới nhiều định dạng khác nhau.

- **Phân tích toàn diện**: Tạo điều kiện cho phân tích dữ liệu lớn và các ứng dụng AI/ML.

- **Tiết kiệm chi phí**: Sử dụng các giải pháp lưu trữ chi phí thấp như Amazon S3.

- **Tích hợp dễ dàng**: Kết nối mượt mà với các công cụ phân tích và báo cáo như Amazon Athena và QuickSight.

#### Thách thức khi triển khai Data Lake

- **Quản Lý Dữ Liệu**: Làm thế nào để tổ chức và quản lý dữ liệu hiệu quả?

- **Bảo Mật**: Làm sao để ngăn chặn truy cập trái phép vào dữ liệu?

- **Khả Năng Mở Rộng**: Hệ thống phải có khả năng mở rộng để xử lý sự gia tăng dữ liệu.

- **Hiệu Suất**: Cần tối ưu hóa cho việc truy vấn và xử lý dữ liệu.

- **Chất Lượng Dữ Liệu**: Đảm bảo tính chính xác và độ tin cậy của dữ liệu là rất quan trọng.

#### Kiến trúc Workshop

##### Tổng quan về kiến trúc

Hình dưới đây minh họa kiến trúc hệ thống Data Lake mà chúng ta sẽ triển khai trong workshop này:
![Workshop](/images/1/workshop.jpg)

##### Mô tả kiến trúc

- Thu thập dữ liệu:

  - Dữ liệu từ nhiều nguồn khác nhau được thu thập qua Kinesis.
  - Kinesis Firehose Stream xử lý và chuyển dữ liệu đến Amazon S3.

- Lưu trữ dữ liệu thô:

  - Dữ liệu thô được lưu trữ trong S3 ở thư mục "raw data".
  - CloudFormation tự động triển khai các tài nguyên cần thiết.

- AWS Glue:

  - AWS Glue Crawler quét dữ liệu thô trong S3 để tạo metadata.
  - Metadata được lưu trữ trong AWS Glue Data Catalog.
  - Một ETL Job (Extract, Transform, Load) xử lý và chuyển đổi dữ liệu thô thành dữ liệu đã qua xử lý.

- Lưu trữ dữ liệu đã xử lý:

  - Dữ liệu đã được chuyển đổi được lưu trong một bucket S3 khác dưới thư mục "processed-data".

- Phân tích và trực quan hóa dữ liệu:

  - AWS Glue Crawler quét dữ liệu đã qua xử lý và cập nhật Glue Data Catalog.
  - Amazon Athena được sử dụng để truy vấn dữ liệu trong S3.
  - Amazon QuickSight kết nối đến dữ liệu để trực quan hóa và báo cáo.

##### Mục tiêu của workshop

- Hiểu các thành phần của kiến trúc Data Lake.
- Triển khai một hệ thống Data Lake đơn giản bằng các dịch vụ AWS.
- Tích hợp các công cụ phân tích và trực quan hóa để trích xuất thông tin hữu ích từ dữ liệu.

{{% notice info %}}
Bài lab này được thực hiện ở region Singapore (ap-southeast-1).
{{% /notice %}}

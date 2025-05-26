+++
title = "Phân tích và trực quan hóa"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

## Amazon Athena

**Amazon Athena** là một dịch vụ truy vấn tương tác được sử dụng để phân tích dữ liệu trong Amazon S3 bằng SQL tiêu chuẩn. Chúng ta chỉ cần trỏ đến dữ liệu của bạn trong Amazon S3, xác định schema và bắt đầu truy vấn bằng trình chỉnh sửa truy vấn tích hợp. Amazon Athena cho phép chúng ta khai thác tất cả dữ liệu của mình trong Amazon S3 mà không cần phải thiết lập các quy trình ETL phức tạp. Amazon Athena tính tiền dựa trên số lượng truy vấn được chạy.

**Amazon Athena** sử dụng Presto với hỗ trợ SQL ANSI và làm việc với nhiều định dạng dữ liệu tiêu chuẩn, bao gồm CSV, JSON, ORC, Avro, và Parquet. Athena được khuyến nghị cho các nhu cầu truy vấn nhanh, nhưng cũng có khả năng xử lý phân tích phức tạp, bao gồm các phép join với lượng dữ liệu lớn, các window function và mảng.

## Amazon QuickSight

**Amazon QuickSight** là một dịch vụ biểu diễn dữ liệu được quản lý hoàn toàn bởi AWS.

- **Data source** là một kho lưu trữ dữ liệu bên ngoài và bạn cần cấu hình việc truy cập dữ liệu trong kho dữ liệu bên ngoài này, ví dụ Amazon S3, Amazon Athena, Salesforce, v.v.

- **Dataset** xác định dữ liệu cụ thể trong Data source mà bạn muốn sử dụng. Ví dụ: Data source có thể là một bảng nếu bạn đang kết nối với cơ sở dữ liệu. Nó có thể là một file nếu bạn đang kết nối với Amazon S3.

- **Analysis** là nơi chứa một tập hợp các Visual và câu chuyện liên quan, ví dụ như tất cả các câu chuyện áp dụng cho một mục tiêu kinh doanh nhất định hoặc KPI.

- **Visual** là một biểu diễn đồ họa của dữ liệu bạn. Bạn có thể tạo nhiều loại Visual khác nhau trong một Analysis, sử dụng các bộ dữ liệu và loại Visual khác nhau.

- **Dashboard** là một trang bao gồm một hoặc nhiều Analysis chỉ cho phép xem, mà bạn có thể chia sẻ với người dùng Amazon QuickSight khác cho mục đích báo cáo. Dashboard giữ cấu hình của bản Analysis tại thời điểm bạn xuất bản nó, bao gồm các yếu tố như lọc, tham số, điều khiển và thứ tự sắp xếp.

## Nội dung:

1. [Phân tích với Athena](6.1-athena)
2. [Visualize với QuickSight](6.2-quicksight)

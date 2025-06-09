+++
title = "Giới thiệu"
date = 2025
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

### Các phương pháp kịch bản phản ứng sự cố tự động

Trong phòng lab này, chúng ta sẽ triển khai hai loại **kịch bản phản ứng sự cố (IR)** tự động bằng cách sử dụng các dịch vụ gốc của AWS. Mỗi phương pháp cung cấp những ưu điểm và điểm đánh đổi riêng, tùy thuộc vào độ phức tạp và thời lượng của các tác vụ khắc phục.

{{% notice note %}}
Phòng lab này được thực hiện tại vùng: us-east-1 (N. Virginia).  
Thời lượng phòng lab khoảng 3 giờ, ngay cả khi bạn không hoàn thành, hãy truy cập phần **dọn dẹp tài nguyên** để tránh bị tính phí.
{{% /notice %}}

##### 1. Kịch bản IR dựa trên Lambda

![Workshop](../../images/1/Workshop_Lambda.jpg)

Phương pháp này sử dụng một hàm **AWS Lambda** để thực hiện các hành động khắc phục ngay khi phát hiện sự cố. Đây là phương pháp **đơn giản và nhanh nhất để triển khai**. Tuy nhiên, nó có điểm hạn chế đáng chú ý:

- **Thời gian thực thi bị giới hạn trong 15 phút**, nghĩa là nó **không thể xử lý các tác vụ kéo dài**, chẳng hạn như chờ một bản sao lưu EBS hoàn tất hoặc thu thập dữ liệu pháp y chi tiết.
- Phù hợp nhất cho các hành động **ngay lập tức và nhẹ nhàng**, như gắn thẻ, cách ly instance bằng cách thay đổi security group, hoặc gửi cảnh báo.

##### 2. Kịch bản IR dựa trên Step Functions

![Workshop](../../images/1/Workshop_Step_Function.jpg)

Phương pháp này sử dụng **AWS Step Functions** để điều phối phản ứng sự cố dưới dạng một **modular state machine**, cho phép một quy trình IR linh hoạt và mạnh mẽ hơn.

- Không giống như Lambda, **không có giới hạn thời gian thực thi**, cho phép xử lý **các quy trình phức tạp, nhiều bước** có thể kéo dài vài phút hoặc thậm chí vài giờ.
- Các tác vụ có thể được chia thành **các trạng thái độc lập và dễ quản lý**, bao gồm thực thi song song, thử lại, điều kiện chờ và logic xử lý lỗi.
- Lý tưởng cho các tình huống yêu cầu **thực hiện theo trình tự**, như tạo bản sao lưu, thu thập dữ liệu pháp y (forensic data), thông báo đến nhiều hệ thống, sau đó chấm dứt hoặc cách ly instance.

Bằng cách so sánh hai phương pháp, bài lab này nổi bật cách các công cụ tự động hóa của AWS có thể được tùy chỉnh để đáp ứng các nhu cầu phản ứng khác nhau — từ phản ứng nhanh đến các quy trình khắc phục toàn diện.

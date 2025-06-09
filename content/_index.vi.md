---
title: 'Tự động hoá phản hồi sự cố'
date: 2025
weight: 1
chapter: false
---

# Tự động hoá phản hồi sự cố

#### Tổng quan

Bài lab này được thiết kế để mô phỏng và phản hồi một sự cố bảo mật trong môi trường cloud, liên quan đến một **EC2 instance bị xâm nhập** trong môi trường AWS. Mục tiêu là xây dựng và triển khai **playbook phản hồi sự cố (IR)** tự động để phát hiện và khắc phục hoạt động độc hại mà không cần can thiệp thủ công, tận dụng các công cụ và dịch vụ gốc của AWS.

#### Tóm tắt kịch bản

Kẻ tấn công đã xâm nhập thành công một EC2 instance, có thể thông qua một lỗ hổng như **OS command injection**. Sau khi truy cập trái phép, kẻ tấn công:

- Cài đặt **TOR client** để giao tiếp ẩn danh với máy chủ điều khiển và điều khiển (C2) bên ngoài.
- Cố gắng thực hiện **đào Bitcoin** và thiết lập kết nối đến **địa chỉ IP độc hại đã biết**.

#### Các phương pháp triển khai Playbook phản hồi sự cố tự động

Trong lab này, chúng ta sẽ triển khai hai phương pháp phản hồi sự cố tự động (IR) sử dụng các dịch vụ gốc của AWS. Mỗi phương pháp có ưu điểm và điểm hạn chế riêng, phù hợp với các tình huống và mức độ phức tạp khác nhau của quá trình xử lý.

##### 1. Playbook IR dựa trên Lambda

Phương pháp này sử dụng một hàm **AWS Lambda** duy nhất để thực hiện các hành động khắc phục ngay khi phát hiện sự cố. Đây là phương pháp **đơn giản và triển khai nhanh nhất**. Tuy nhiên, nó có một giới hạn quan trọng:

- **Thời gian thực thi bị giới hạn ở 15 phút**, do đó **không phù hợp với các tác vụ kéo dài**, như chờ sao lưu EBS hoàn tất hoặc thu thập dữ liệu pháp y (forensic data) chi tiết.
- Thích hợp cho các hành động **nhẹ và tức thời**, như gắn thẻ, cách ly instance bằng cách thay đổi security group, hoặc gửi cảnh báo.

##### 2. Playbook IR dựa trên Step Functions

Phương pháp này sử dụng **AWS Step Functions** để điều phối phản hồi sự cố dưới dạng **modular state machine**, cho phép quy trình IR linh hoạt và mạnh mẽ hơn.

- Không giống như Lambda, phương pháp này **không bị giới hạn thời gian thực thi nghiêm ngặt**, cho phép các workflow **phức tạp, nhiều bước**, có thể kéo dài hàng phút hoặc hàng giờ.
- Các tác vụ được chia thành các **state độc lập và dễ quản lý**, hỗ trợ thực thi song song, retry, delay, và xử lý lỗi.
- Phù hợp với các tình huống cần hành động theo trình tự như tạo snapshot, thu thập dữ liệu pháp y, gửi thông báo cho nhiều hệ thống, sau đó tiến hành cách ly hoặc xoá instance.

Thông qua việc so sánh hai phương pháp, lab này sẽ cho thấy cách các công cụ tự động hoá của AWS có thể được tuỳ chỉnh để đáp ứng nhu cầu phản hồi — từ phản ứng nhanh đến khắc phục toàn diện.

#### Mục tiêu của Workshop

Sau khi hoàn thành workshop này, bạn sẽ:

- Thực hiện được các tác vụ phản hồi sự cố cơ bản một cách tự động, tập trung vào **khoanh vùng (containment)** và **thu thập dữ liệu pháp y (forensic data collection)**.  
- Hiểu được các hành động khắc phục có thể thực hiện và mức độ công sức cần thiết.

{{% notice info %}}
Thời lượng workshop khoảng 3 giờ, ngay cả khi bạn không hoàn thành, hãy truy cập phần **xoá tài nguyên** để tránh phát sinh chi phí.
{{% /notice %}}

#### Nội dung Workshop

1. [Giới thiệu](1-Introduction)
2. [Các bước chuẩn bị](2-Preparation)
3. [Cấu hình phản hồi](3-Configure-Response)
4. [Cấu hình phản hồi tự động](4-Configure-Automated-Response)
5. [Xoá tài nguyên](5-Clean-up)

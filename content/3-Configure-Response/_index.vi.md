+++
title = "Cấu hình phản hồi"
date = 2025
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

Trong phần này, bạn sẽ triển khai hành động phản hồi tự động cho sự cố theo hai cách khác nhau:

- Trên một AWS Lambda function duy nhất: đây là cách đơn giản nhất để thực thi các bước khắc phục, nhưng có hạn chế là không thể chờ các tác vụ như snapshot hoàn thành vì Lambda bị giới hạn timeout 15 phút.

- Trên State Machine thông qua Step Functions: đây là lựa chọn phức tạp hơn nhưng linh hoạt hơn vì có thể cấu hình phản hồi theo dạng mô-đun. Không có giới hạn về hành động hay thời gian chạy của State Machine.

#### Nội dung:

1. [Single Lambda response](3.1-Single-Lambda-response)  
2. [Step Function response](3.2-Step-Function-response)

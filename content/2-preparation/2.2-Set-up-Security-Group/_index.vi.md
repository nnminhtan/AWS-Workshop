+++
title = "Thiết lập Security Group"
date = 2025
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

<!-- ## Thiết lập Security Group -->

Tiếp theo, chúng ta sẽ tạo một Security Group.

1. Truy cập **Security group**

   - Tìm kiếm **Security group**, nhấn vào **Security group**.

   ![SG](/images/2/2.2/Access_SG.png)

   - Chọn **Create security group**.

   ![SG](/images/2/2.2/Create_SG.png)

2. Trong giao diện **Create security group**, tại phần **Basic details**

   - Tại _Security group name_, đặt tên là: `ForensicsSG`.
   - Đảm bảo chọn đúng **VPC** là _(VPC-AutomatedIncidentResponeWorkshop)_ như hình bên dưới.
   
   ![SG](/images/2/2.2/Create_SG_basic_detail.png)

3. Trong phần **Inbound rules and Outbound rules**

   - Tại _Inbound rules_, thêm các **Inbound rules** mới như sau:
     - RDP TCP 3389 Source: (địa chỉ IP của bạn) Description (tuỳ chọn): `RDP for IR team`.
     - SSH TCP 22 Source: (địa chỉ IP của bạn) Description (tuỳ chọn): `SSH for IR team`.
   - Xoá toàn bộ **Outbound rules** như hình dưới.

   ![SG](/images/2/2.2/Create_SG_rules.png)

   - Nhấn **Create security group**.

4. Policy đã được tạo thành công:

   ![Policy](/images/2/2.2/Create_SG_success.png)

Sau khi tạo Security Group xong, hãy sao chép **Security group ID** và chuyển sang bước tiếp theo [Tạo IAM user để kiểm thử](../2.3-Create-an-IAM-user-for-Testing)

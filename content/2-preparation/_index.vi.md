+++
title = "Các bước chuẩn bị"
date = 2025
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

<!-- ## Các bước chuẩn bị -->

Chúng ta sẽ chuẩn bị bằng cách tạo một IAM user để kiểm tra và gán các policy cần thiết. Bạn sẽ bật Amazon GuardDuty và triển khai CloudFormation template để tạo hạ tầng mẫu nhằm mô phỏng kẻ tấn công và mục tiêu.

{{% notice warning %}}
Đảm bảo rằng tài khoản được sử dụng cho workshop này **KHÔNG phải là production account**.
{{% /notice %}}

#### Nội dung:

1. [Triển khai CloudFormation stack](2.1-Deploy-the-CloudFormation-stack)
2. [Thiết lập Security Group](2.2-Set-up-Security-Group)
3. [Tạo IAM user để kiểm thử](2.3-Create-an-IAM-user-for-Testing)

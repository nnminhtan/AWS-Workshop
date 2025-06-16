+++
title = "Phản hồi bằng Lambda"
date = 2020
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

### Cấu hình phản hồi bằng một Lambda function

Trong phần này, bạn sẽ học cách triển khai hành động phản hồi sự cố tự động trên một AWS **Lambda Function** duy nhất. Hàm này sẽ thực hiện tất cả các hành động cần thiết trong cùng một đoạn mã.

Các bước thực hiện bao gồm:

- Tạo **IAM policy** và đính kèm vào **IAM role** mà **Lambda function** sẽ sử dụng để thực thi các phản hồi tự động.
- Tạo _Lambda function_.
- Kiểm thử _Lambda function_.
- Tạo **EventBridge rule** để gọi _Lambda function_ dựa trên các phát hiện từ **GuardDuty**.

Kiến trúc cho phương án này như sau:  
![Lambda](../../../images/1/Workshop_Lambda.jpg?width=90pc)

#### Nội dung:

1. [Tạo IAM Policies và Roles](3.1.1-Create-IAM-Policies-and-Roles)  
2. [Tạo Lambda Function](3.1.2-Create-Lambda-Function)  
3. [Kiểm thử Lambda Function](3.1.3-Test-Lambda-Function)  
4. [Tạo EventBridge Rule](3.1.4-Create-EventBridge-Rule)


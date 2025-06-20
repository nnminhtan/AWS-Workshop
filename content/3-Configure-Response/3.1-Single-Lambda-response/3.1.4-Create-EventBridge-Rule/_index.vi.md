+++
title = "Tạo EventBridge Rule"
date = 2025
weight = 4
chapter = false
pre = "<b>3.1.4. </b>"
+++

Trong bước này, chúng ta sẽ tạo một EventBridge Rule để tự động tạo snapshot cho **BasicLinuxTarget**.

<!-- #### **Tạo EventBridge Rule**: -->

#### Tạo EventBridge Rule
- Tìm kiếm **EventBridge**. Bạn sẽ được dẫn đến trang chủ EventBridge, nhấn vào **Create Rule**.

![EventBridge](../../../../images/3/3.1/3.1.4/Create_rule.png?width=90pc)

- Đặt tên rule là: `gd-compromised-instance-remediation`, phần mô tả có thể bỏ trống, sau đó tiếp tục tạo.

![EventBridge](../../../../images/3/3.1/3.1.4/Create_rule_naming.png?width=90pc)

- Ở phần _Event pattern_, dưới _Creation method_ chọn **Custom pattern (JSON editor)**, dán đoạn JSON vào editor.  
```json
{
    "source": ["aws.guardduty"],
    "detail": {
        "type": ["UnauthorizedAccess:EC2/TorClient", "Backdoor:EC2/C&CActivity.B!DNS", "Trojan:EC2/DNSDataExfiltration", "CryptoCurrency:EC2/BitcoinTool.B", "CryptoCurrency:EC2/BitcoinTool.B!DNS"]
    }
}
```
- Kết quả sẽ như hình bên dưới, rồi nhấn **Next**.

![EventBridge](../../../../images/3/3.1/3.1.4/Create_rule_event_pattern.png?width=90pc)

1. Chọn **Lambda function** làm target.
2. Chọn function **ec2instance-containment-with-forensics** làm Function. (Kết quả sẽ như hình)

![EventBridge](../../../../images/3/3.1/3.1.4/Create_rule_event_target.png?width=90pc)

3. Giữ nguyên các thiết lập còn lại và tạo Rule.

{{% notice note %}}
Hãy chắc chắn rằng instance đã được cách ly trước khi tạo snapshot, nếu không bạn có thể bị tạo nhiều snapshot liên tục mỗi 15 phút (hoặc 6 tiếng tùy cấu hình GuardDuty). Tác giả khuyến nghị nên tắt rule này sau khi hoàn tất quá trình testing.
{{% /notice %}}

Khi bạn đã hoàn thành tất cả các bước, hãy chuyển sang phần tiếp theo của Workshop là [Câu hình phản hồi tự động](../../../../4-Configure-Automated-Response) hoặc bạn có thể thực hiện [Phản hồi bằng Step Function](../../3.2-Step-Function-response).

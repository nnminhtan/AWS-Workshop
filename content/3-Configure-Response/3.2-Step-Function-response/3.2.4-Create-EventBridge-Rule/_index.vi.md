+++
title = "Tạo EventBridge Rule"
date = 2025
weight = 4
chapter = false
pre = "<b>3.2.4. </b>"
+++

Trong bước này, chúng ta sẽ tạo một EventBridge Rule để tạo snapshot cho **BasicLinuxTarget**.

<!-- #### **Tạo EventBridge Rule**: -->

#### Tạo EventBridge Rule
- Tìm kiếm dịch vụ EventBridge. Truy cập vào trang chính của EventBridge, sau đó nhấn **Create Rule**.

![EventBridge](/images/3/3.1/3.1.4/Create_rule.png?width=90pc)

- Đặt tên cho rule là: `gd-compromised-instance-remediation` (nếu bạn vẫn giữ rule cũ thì thêm hậu tố `-sf`), phần mô tả là tùy chọn, sau đó tiếp tục tạo rule.

![EventBridge](/images/3/3.1/3.1.4/Create_rule_naming.png?width=90pc)

- Trong mục _Event pattern_, _Creation method_ chọn _Custom pattern (JSON editor)_ và dán nội dung JSON bên dưới vào editor
```json
{
    "source": ["aws.guardduty"],
    "detail": {
        "type": ["UnauthorizedAccess:EC2/TorClient", "Backdoor:EC2/C&CActivity.B!DNS", "Trojan:EC2/DNSDataExfiltration", "CryptoCurrency:EC2/BitcoinTool.B", "CryptoCurrency:EC2/BitcoinTool.B!DNS"]
    }
}
```
- Kết quả sẽ như thế này, sau đó nhấn **Next**.

![EventBridge](/images/3/3.1/3.1.4/Create_rule_event_pattern.png?width=90pc)

1. Chọn **Step Functions state machine** làm mục tiêu (target).
2. Chọn _**State Machine**_ mà chúng ta đã kiểm thử trước đó (**PREFIX_StateMachine**) làm Target. (Kết quả sẽ trông như hình dưới)

![EventBridge](/images/3/3.2/3.2.4/Create_rule_target.png?width=90pc)

3. Giữ nguyên các thiết lập còn lại và nhấn **Create Rule** để hoàn tất.

{{% notice note %}}
Hãy đảm bảo rằng instance đã được cách ly trước khi tạo snapshot, nếu không bạn có thể gặp tình trạng snapshot bị tạo liên tục mỗi 15 phút 
(hoặc 6 giờ tùy theo cấu hình GuardDuty của bạn). Tác giả khuyến nghị bạn nên vô hiệu hóa rule này sau khi đã hoàn thành việc kiểm thử.
{{% /notice %}}

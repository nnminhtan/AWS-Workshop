+++
title = "Create EventBridge Rule"
date = 2025
weight = 4
chapter = false
pre = "<b>3.2.4. </b>"
+++

In this step we will create a EventBridge Rule for create a snapshot for the **BasicLinuxTarget**.

<!-- #### **Create EventBridge Rule**: -->

#### Create EventBridge Rule
- Search for the EventBridge. This will take you to the EventBridge home, click on Create Rule.

![EventBridge](../../../images/3/3.1/3.1.4/Create_rule.png?width=90pc)

- Name the rule is : `gd-compromised-instance-remediation` (if you still kept the old one then add this rule with `-sf`), the description is optional, then foward to the creation.

![EventBridge](../../../images/3/3.1/3.1.4/Create_rule_naming.png?width=90pc)

- Under _Event pattern_, _Creation method_ click the _Custom pattern(JSON editor)_ and paste the **Json** below into the editor.
```json
{
    "source": ["aws.guardduty"],
    "detail": {
        "type": ["UnauthorizedAccess:EC2/TorClient", "Backdoor:EC2/C&CActivity.B!DNS", "Trojan:EC2/DNSDataExfiltration", "CryptoCurrency:EC2/BitcoinTool.B", "CryptoCurrency:EC2/BitcoinTool.B!DNS"]
    }
}
```
- The result should be like this then click _Next_.

![EventBridge](../../../images/3/3.1/3.1.4/Create_rule_event_pattern.png?width=90pc)

1. Select **Step Functions state machine** as the target.
2. Select the the _**State Machine**_ that we tested before **PREFIX_StateMachine** as the Target. (The result should be like this)

![EventBridge](../../../images/3/3.2/3.2.4/Create_rule_target.png?width=90pc)

3. Leave every unchanged and create the Rule.

{{% notice note %}}
Make sure the instance is already isolated before taking snapshots otherwise you may end up with many snapshots created every 15 minutes 
(or 6H depending your GuardDuty setting). The author recommend disabling this rule once you've completed the testing.
{{% /notice %}}

When you are done with all the steps, head to the next part of the Workshop which is [Configure Automated Response](../../../4-Configure-Automated-Response)
+++
title = "Configure Automated Response"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Configure Automated Response

In this section you will know how to ingest sample findings using **GuardDuty** and use the input for the automated incident response process.

In the environment there is a _"RedTeam"_ instance that will generate **GuardDuty** findings.

1. Go to **GuardDuty**, select **Settings**.
2. Under _Findings export options_, the prequency should be update findings every 15 mins if you using the CloudFormation template. (If not Click _Edit_ set the Frequency to set it to update every 15 mins).
![GuardDuty](/images/4/GuardDuty_frequency.png?width=90pc)

3. Then select **findings**.

{{% notice note %}}
You have to wait for a while for it to get the findings, also other service running might raise the cost if you don't want to wait then you can skip this (optional!). But here is the sample results should look like.
{{% /notice %}}

![GuardDuty](/images/4/GuardDuty_findings.png?width=90pc)


#### Test Automated Response

To test the automated response, you could

1. Wait for the RedTeam instance to trigger the event, as it's using the [GuardDuty tester scripts](https://github.com/awslabs/amazon-guardduty-tester) 

2. You could manually launch a Windows instance creating a new SG that allows RDP (3389) access from your IP Address, and simulate outgoing malware connections by:

   - Installing a [TOR Browser](https://www.torproject.org/download/)
   - Connecting to mining pools like `pool.minergate.com`

3. You could manually launch a Linux instance creating a new SG that allows SSH (22) access from your IP Address, and call the fake domain introduced in our threat intelligence feeds that is used to test Command & Control Findings with the following command:

```
dig GuardDutyC2ActivityB.com any
```

4. Wait a couple of minutes (it can take up to 20 min) for **GuardDuty** to generate the findings .

{{% notice note %}}
If you choose Linux instances, you can use EC2 Instance Connect to get a terminal on the instance or connecting using SSH.
{{% /notice %}}

{{% notice note %}}
To connect to the RedTeam instance you can use Systems Manager Session Manager, but you'd have to add the instance profile for SSM, and reboot the instance.
{{% /notice %}}



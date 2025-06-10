+++
title = "Introduction"
date = 2025
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

### Automated Incident Response Playbook Approaches

In this lab, we will implement two types of automated incident response (IR) playbooks using AWS-native services. Each approach provides distinct advantages and trade-offs depending on the complexity and duration of the remediation tasks.

{{% notice note %}}
This workshop is test in the region: us-east-1 (N. Virginia).
This workshop length is around 3hrs, even if you dont complete it visit the **clean up resources** part to avoid the fees.
{{% /notice %}}

##### 1. Lambda-based IR Playbook

![Workshop](../images/1/Workshop_Lambda.jpg)

This approach uses a **single AWS Lambda function** to execute remediation actions as soon as an incident is detected. It is the **simplest and fastest method** to deploy. However, it comes with an important limitation:

- **Execution time is capped at 15 minutes**, which means it **cannot accommodate long-running tasks**, such as waiting for an EBS snapshot to complete or performing detailed forensic collection.
- Best suited for **immediate and lightweight actions**, such as tagging, isolating the instance via security group changes, or sending alerts.

##### 2. Step Functions-based IR Playbook

![Workshop](../images/1/Workshop_Step_Function.jpg)

This method uses **AWS Step Functions** to orchestrate the incident response as a **modular state machine**, enabling a more flexible and robust IR process.

- Unlike Lambda, **there is no strict execution timeout**, allowing for **complex, multi-step workflows** that may span several minutes or even hours.
- Tasks can be broken into **independent, manageable states**, including parallel execution, retries, wait conditions, and failure handling logic.
- Ideal for scenarios requiring **sequenced actions**, such as taking snapshots, gathering forensic data, notifying multiple systems, and then terminating or quarantining the instance.

By comparing both approaches, this lab highlights how AWS automation tools can be tailored to meet different response needs from rapid reaction to comprehensive remediation pipelines.


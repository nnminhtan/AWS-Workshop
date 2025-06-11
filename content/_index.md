---
title: 'Automating Incident Response'
date: 2025
weight: 1
chapter: false
---

# Automating Incident Response

#### Overview

This lab is designed to simulate and respond to a real-world cloud security incident involving a compromised EC2 instance within the AWS environment. The focus is on building and executing **automated incident response (IR)** playbooks to detect and remediate malicious activity without manual intervention, leveraging AWS-native tools and services.

#### Scenario Summary

An adversary has successfully compromised an EC2 instance, potentially via a vulnerability such as an **OS command injection**. After gaining unauthorized access, the attacker:

- Installs a **TOR client** to communicate anonymously with an external command-and-control (C2) server.
- Attempts to perform **Bitcoin mining** and establish a connection to **a known malicious IP address**.

#### Automated Incident Response Playbook Approaches

In this lab, we will implement two types of automated incident response (IR) playbooks using AWS-native services. Each approach provides distinct advantages and trade-offs depending on the complexity and duration of the remediation tasks.

##### 1. Lambda-based IR Playbook

This approach uses a **single AWS Lambda function** to execute remediation actions as soon as an incident is detected. It is the **simplest and fastest method** to deploy. However, it comes with an important limitation:

- **Execution time is capped at 15 minutes**, which means it **cannot accommodate long-running tasks**, such as waiting for an EBS snapshot to complete or performing detailed forensic collection.
- Best suited for **immediate and lightweight actions**, such as tagging, isolating the instance via security group changes, or sending alerts.

##### 2. Step Functions-based IR Playbook

This method uses **AWS Step Functions** to orchestrate the incident response as a **modular state machine**, enabling a more flexible and robust IR process.

- Unlike Lambda, **there is no strict execution timeout**, allowing for **complex, multi-step workflows** that may span several minutes or even hours.
- Tasks can be broken into **independent, manageable states**, including parallel execution, retries, wait conditions, and failure handling logic.
- Ideal for scenarios requiring **sequenced actions**, such as taking snapshots, gathering forensic data, notifying multiple systems, and then terminating or quarantining the instance.

By comparing both approaches, this lab highlights how AWS automation tools can be tailored to meet different response needs from rapid reaction to comprehensive remediation pipelines.

#### Goals of the Workshop

By the end of this workshop, you will have learned how to:
- Perform automated basic incident response tasks focused on **containment** and **forensic data collection**.  
- Understand the range of possible remediation actions and the effort involved in executing them.

{{% notice info %}}
This workshop length is around 3hrs, even if you dont complete it visit the **clean up resources** part to avoid the fees.
{{% /notice %}}

#### Workshop Content

1. [Introduction](1-Introduction)
2. [Preparation Steps](2-Preparation)
3. [Configure Response](3-Configure-Response)
4. [Configure Automated Response](4-Configure-Automated-Response)
5. [Clean Up Resources](5-Clean-up)

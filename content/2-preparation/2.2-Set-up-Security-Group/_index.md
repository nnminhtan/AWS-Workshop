+++
title = "Set up Security Group"
date = 2025
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

<!-- ## Set up Security group -->

Next, we will create a Security group.

1. Access the **Security group** 

   - Search for the  **Security group**.
   - Click **Security group**.

   ![SG](/images/2/2.2/Access_SG.png)

   - Select the **Create security group**.

   ![SG](/images/2/2.2/Create_SG.png)

2. In the **Create security group** interface, under **Basic details**

   - Under _Security group name_, set the name as :  `ForensicsSG`.
   - Make sure to set the **VPC** to _(VPC-AutomatedIncidentResponeWorkshop)_ as shown below.
   
   ![SG](/images/2/2.2/Create_SG_basic_detail.png)

3. In the **Create security group** interface, under **Inbound rules and Outbound rules**
   
   - Under the _Inbound rules_, add new **Inbound rules** and set as below.
   - RDP    TCP   3389  Source (your IP)  Description(optional) : `RDP for IR team`.
   - SSH    TCP   22    Source (your IP)  Description(optional) : `SSH for IR team`.
   - Remove all of the **Outbound rules** as below.

   ![SG](/images/2/2.2/Create_SG_rules.png)

   - Click **Create security group**.

4. Policy created successfully:

   ![Policy](/images/2/2.2/Create_SG_success.png)
   
After Security group creation is complete, copy the **Security group ID** and go to the next step [Create an IAM user for Testing](../2.3-Create-an-IAM-user-for-Testing)
   
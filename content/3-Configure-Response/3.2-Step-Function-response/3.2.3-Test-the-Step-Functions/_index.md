+++
title = "Test the Step Functions"
date = 2025
weight = 3
chapter = false
pre = "<b>3.2.3. </b>"
+++

<!-- #### Test Lambda Function: -->

In this step we will test the Step Functions that created previously.

1. Go to the **Step Functions** service and on **States machines** select the name of the newly created one _**PREFIX_StateMachine**_.
   
   ![Test SF](../../../images/3/3.2/3.2.3/State_machine.png?width=90pc)
   
2. Select **Start execution**
   
   ![Test SF](../../../images/3/3.2/3.2.3/Start_execution.png?width=90pc)

    - Copy this JSON below and paste in _Input_, this JSON will need some modifications before you can run it.
    
    ```json
    {
        "version": "0",
        "id": "cd2d702e-ab31-411b-9344-793ce56b1bc7",
        "detail-type": "GuardDuty Finding",
        "source": "aws.guardduty",
        "account": "<<Account ID>>",
        "time": "1970-01-01T00:00:00Z",
        "region": "us-east-1",
        "resources": [],
        
        "detail": {
            "schemaVersion": "2.0",
            "accountId": "<<Account ID>>",
            "region": "us-east-1",
            "partition": "aws",
            "id": "b0baa89de4ab301f8d0a8c9a3dfd5726",
            "arn": "arn:aws:guardduty:us-east-1:<<Account ID>>:detector/feb3c048238f682b8902532ec100b3fb/finding/b0baa89de4ab301f8d0a8c9a3dfd5726",
            "title": "Bitcoin-related domain name queried by EC2 instance <<Instance ID>>.",
            "type": "CryptoCurrency:EC2/BitcoinTool.B!DNS",
            "severity": 8,
            "resource": {
                "instanceDetails": {
                    "instanceId": "<<Instance ID>>"
                }
            }
        }
    }
    ```

      - Replace the **AccountID** for yours.
      - Replace the **Instance ID** with the ID of the BasicLinuxTarget instance deployed by the CloudFormation template (below is how you can find the _Instance ID_).

    ![Test SF](../../../images/3/3.1/3.1.3/Create_test_event_InstanceID.png?width=90pc)
    
    - After replace all the **Account ID** and **Instance ID**.

    ![Test SF](../../../images/3/3.2/3.2.3/Start_execution_modification.png?width=90pc)

    - Verify status _before execution_: check on the **EC2 console** what is the current status of the instance **"BasicLinuxTarget"**

    {{% notice note %}}
    Can you answer the following questions?
        • Which Security Group does it have?
        • Which tags does it have ?
        • Is there any snapshot related to the instance?
    {{% /notice %}}

    - Press the _Start execution_, and verify the status _after execution_: of the instance **"BasicLinuxTarget"**

    {{% notice note %}}
    Can you answer the following questions?

        • Has the Security Group changed?
        • Have the tags changed?
        • Has any new Snapshot been created?
        • Log in with a different Internet browser or using private mode, use the link on the IAM Dashboard (as seen below) and verify if you can delete the EC2 with the IAM user testuser that you created during the Setup steps.
            
            • Are you able to delete the instance?
    {{% /notice %}}
        ![Test SF](../../../images/3/3.1/3.1.3/testuser_signin.png?width=90pc)

    - When you use the _testuser_ and try to delete the instance **"BasicLinuxTarget"** it should have this error.
    
    ![Test SF](../../../images/3/3.1/3.1.3/testuser_delete.png?width=90pc)

3. Test the State Machine with a different severity
    - Follow the same steps as before but change the **severity** field on the JSON event from 8 to 7.
      - Is the workflow executed still the same?
      - What changed?

When you are done with all the steps, head to the next part of the Workshop which is [Create a EventBridge Rule](../3.2.4-Create-EventBridge-Rule)

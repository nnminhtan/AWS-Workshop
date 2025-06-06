+++
title = "Test Lambda Function"
date = 2025
weight = 3
chapter = false
pre = "<b>3.1.3. </b>"
+++

<!-- #### Test Lambda Function: -->

In this step we will test the Lambda Function that created previously.

1. Review the comments on the code to understand what it's doing.

    - Review the main steps on the code. Note: this is just an example, more actions could be added.
    - The code has several print functions that you can leave enabled to see the contents on CloudWatch Logs, or you can comment them out.

2. Create **test event** for Lambda function

    - In the same _Function code editor_,  
    - Select **Test** this will open a **Create new test event** on the top, click on it.

    ![Test Lambda](/images/3/3.1/3.1.3/Create_test_event.png?width=90pc)

    - The panel _Create new test event_ will open, name the _test event_ : `GuardDutyViaCWE`.
    - Copy this JSON below and paste in _Event JSON_, this JSON will need some modifications before you can run it.
    
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
            "type": "UnauthorizedAccess:EC2/TorClient",
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

    ![Test Lambda](/images/3/3.1/3.1.3/Create_test_event_InstanceID.png?width=90pc)
    
    - After replace all the Account ID and Instance ID, then save.

    ![Test Lambda](/images/3/3.1/3.1.3/Create_test_event_modification.png?width=90pc)

    - Verify status _before execution_ : check on the EC2 console what is the current status of the instance **"BasicLinuxTarget"**

    {{% notice note %}}
    Can you answer the following questions?

        • Which Security Group does it have?
        • Which tags does it have ?
        • Is there any snapshot related to the instance?
    {{% /notice %}}

    - Press the test event just created, and verify the status _after execution_: of the instance **"BasicLinuxTarget"**
    
    ![Test Lambda](/images/3/3.1/3.1.3/Test_event.png?width=90pc)

    {{% notice note %}}
    Can you answer the following questions?

        • Has the Security Group changed?
        • Have the tags changed?
        • Has any new Snapshot been created?
        • Log in with a different Internet browser or using private mode, use the link on the IAM Dashboard 
        (as seen below) and verify if you can delete the EC2 with the IAM user testuser that you created during the Setup steps.
            
            • Are you able to delete the instance?
    {{% /notice %}}
        ![Test Lambda](/images/3/3.1/3.1.3/testuser_signin.png?width=90pc)

    - When you use the _testuser_ and try to delete the instance **"BasicLinuxTarget"** it should have this error.
    
    ![Test Lambda](/images/3/3.1/3.1.3/testuser_delete.png?width=90pc)

When you are done with all the steps, head to the next part of the Workshop which is [Create a EventBridge Rule](../3.1.4-Create-EventBridge-Rule)

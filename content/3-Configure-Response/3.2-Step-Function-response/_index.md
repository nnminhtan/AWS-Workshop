+++
title = "Step Function response"
date = 2025
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

### Configure for Step Function response

In this section you will learn how to implement an automated incident response action via a workflow implemented with Step Functions. The advantages of this approach are:
   - No timeout for the actions to be performed
   - Almost all the API calls for the AWS Services are implemented and can be directly called without a line of code
   - Graphical workflow definition
   - More control over the different paths

The steps we will be performing for this alternative are:
   - Deploy a CloudFormation template that will create all the necessary resources
   - Accept the SNS subscription in order to receive the email notifications
   - Test the State Machine.
   - Create an EventBridge rule that will call the State Machine based on the GuardDuty findings.

The architecture for this alternative is the following:
   ![SF](/images/1/Workshop_Step_Function.jpg?width=90pc)

And the Step Function workflow graph is the following:
   ![SF](/images/1/.jpg?width=90pc)

A brief explanation of the workflow presented:

1. Check if an _instance ID_ is present on the **GuardDuty** finding
2. Depending on the **GuardDuty** finding severity:

   - If the severity is **higher or equal to 8** then a _SNS notification_ is sent to the registered email (the one used during the CloudFormation deployment).
   - If the severity is **lower than 8** then a _Manual Approval_ email is sent to the registered email:
      - If the _Manual Approval_ is **Rejected** then the workflow is finished and no actions is taken.
      - If the _Manual Approval_ is **Approved** then the following actions are taken.

3. Disable termination is applied to the EC2 instance.
4. Shutdown behavior is changed to the instance.
5. The _ForensicSG Security Group_ is applied to the instance.
6. A tag isolated is applied to the instance.
7. The workflow is finished.


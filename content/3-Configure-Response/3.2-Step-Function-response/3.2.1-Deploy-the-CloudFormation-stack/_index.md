+++
title = "Deploy the CloudFormation stack"
date = 2025
weight = 1
chapter = false
pre = "<b>3.2.1. </b>"
+++


<!-- #### Create IAM Policies & Roles: -->
To initiate the scenario and create the infrastructure we need to deploy a CloudFormation template.

{{% notice info %}}
You can download: [The CloudFormation template](/files/IRWorkshop-StepFunctionsResponse.yaml) file with the required architecture.
{{% /notice %}}

1. Access the [CloudFormation](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create)

   - Search for **CloudFormation**.
   - Select **CloudFormation** to open the **CloudFormation Dashboard**.

   ![CloudFormation](/images/2/2.1/CloudFormation.png)

2. In the **CloudFormation** Dashboard

   - Select **Stacks**.
   - Click **Create stack**.

   ![CloudFormation](/images/2/2.1/Stack.png?width=90pc)

3. In the **Create stack** interface, under **Create stack**

   - Choose **Choose an existing template**.
   - Under _Specify template_, select **Upload a template file**.
   - Click **Choose file** and upload the _IRWorkshop-StepFunctionsResponse.yaml_ file above.
   - Click **Next**.

   ![CloudFormation](/images/3/3.2/3.2.1/Create_stack.png?width=90pc)

4. In the **Specify stack details** interface, under **Specify stack details**

   - Under _Provide a stack name_, Enter **Stack name**: `workshop-IR-StepFunctions`.
   - Under _Parameters_, Enter a **valid email address** and an **optional prefix** for the resouces that will be created.
   - Click **Next**.

   ![CloudFormation](/images/3/3.2/3.2.1/Specify_stack_details.png?width=90pc)

5. In the **Configure stack options** interface, under **Capabilities**

   - **Check yes** for the box below.
    ![CloudFormation](/images/3/3.2/3.2.1/Capabilities.png?width=90pc)

6. In the **Review and create**:
   - If you follow the steps It's should be right so scroll down and click the **Submit** button.
   - Before moving on, make sure the stack is in a **CREATE_COMPLETE** status.

{{% notice note %}}
This should take a couple minutes, so go grab a coffee while at it.
{{% /notice %}}

   ![CloudFormation](/images/3/3.2/3.2.1/Stack_create_complete.png?width=90pc)

If the stack status is **CREATE_COMPLETE** go to the next step [Set up SNS subscription](../3.2.2-SNS-subscription)


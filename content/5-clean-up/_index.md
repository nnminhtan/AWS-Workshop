+++
title = "Cleanup Resources"
date = 2021-06-08T18:57:03+07:00
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

#### Cleaning up resources

In order to prevent charges to your account we recommend cleaning up the infrastructure that was created during this workshop. If you plan to keep things running so you can examine the workshop later, remember to do the cleanup when you are done.

{{% notice note %}}
Please note that you will need to manually delete some resources before you delete the CloudFormation stacks, so please **_do the following steps in order_**.
{{% /notice %}}

1. Disable _termination protection_ for the applicable **EC2 instances**.
    - Open the **EC2 console**.
    - Select the instance.
    - Click on **Actions**, **Instance settings**, change **termination protection**.

    ![CleanUp](../images/5/Instance_delete_1.png?width=90pc)

    - Uncheck the **Enable checkbox**, click **Save**.
    
    ![CleanUp](../images/5/Instance_delete_2.png)

2. Delete the **Cloudformation stack**.
    - Go to the AWS **CloudFormation console**.
    - Select the appropiate stack (remember that depending on the automated responses deployed you might have 2 stacks and 1 nested stack).
    - Click **Delete**.
    
    ![CleanUp](../images/5/Delete_stack.png?width=90pc)

{{% notice warning %}}
Make sure the Stack delete status is **DELETE_COMPLETE**, this could take a while.
{{% /notice %}}

3. Check if Amazon **GuardDuty** was disabled automatically or you need to disable it manually.
    - Go to the **GuardDuty** console.
    - Click on _Settings_ (on the left panel menu).
    - Scroll down.
    - Click **Disable GuardDuty**.
    
    ![CleanUp](../images/5/GuardDuty_disable.png?width=90pc)

{{% notice note %}}
Disabling GuardDuty will remove its data.
{{% /notice %}}

4. Verify and delete any remaining **EC2 snapshots** generated.

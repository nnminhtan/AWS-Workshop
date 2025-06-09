+++
title = "SNS subscription"
date = 2025
weight = 2
chapter = false
pre = "<b>3.2.2. </b>"
+++

<!-- #### SNS subscription -->

As part of the **CloudFormation stack** you just created, you will receive a email like this in the _address_ you entered during the template deployment:

![SNS](../../../images/3/3.2/3.2.2/Subscription-confirmation.png?width=90pc)

You should click on the _Confirm Subscription_ in order to be able to receive the notifications that the **State Machine** will send as part of the automated response. Once you confirm the subscription you should see the following message on the opened webpage:

![SNS](../../../images/3/3.2/3.2.2/Subscription-confirmed.png?width=90pc)

{{% notice note %}}
It might take a few minutes for the email to be delivered. Also check the SPAM folder just in case.
{{% /notice %}}

If you done with that, the next step which we will [Test the Step Functions](../3.2.3-Test-the-Step-Functions).

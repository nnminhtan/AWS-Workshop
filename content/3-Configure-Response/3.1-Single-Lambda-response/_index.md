+++
title = "Single Lambda response"
date = 2025
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

## Configure for single Lambda response

In this section you will learn how to implement an automated incident response action on a single AWS Lambda Function. This function will perform all the necessary actions in the same code.

The steps we will be performing are:

   - Create an IAM policy and attach it to the IAM role that the Lambda function will assume for the automated responses.
   - Create the Lambda function.
   - Test the Lambda function.
   - Create an EventBridge rule that will call the Lambda function based on the GuardDuty findings.

The architecture for this alternative is the following:
   ![Lambda](/images/1/Workshop_Lambda.jpg?width=90pc)

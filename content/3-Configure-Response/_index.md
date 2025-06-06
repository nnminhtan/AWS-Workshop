+++
title = "Configure-Response"
date = 2025
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

In this section you will learn how to implement an automated incident response action in two different ways:

- On a single AWS Lambda function: this is the simplest way to execute the remediation, but it has as caveat that we can't wait for tasks like snapshots to complete as we can hit the 15min Lambda timeout.

- On a State Machine via Step Functions : this is a more complex yet more flexible option as we can configure the response in a modularized way. There is no limitation on neither the actions nor the time the State Machine can be in a running state.

#### Contents:

1. [Single Lambda response](3.1-Single-Lambda-response)
2. [Step Function response](3.2-Step-Function-response)


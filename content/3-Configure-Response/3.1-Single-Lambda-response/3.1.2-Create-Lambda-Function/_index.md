+++
title = "Create Lambda Function"
date = 2025
weight = 2
chapter = false
pre = "<b>3.1.2. </b>"
+++

<!-- #### Create Lambda Function -->

1. Create a **Lambda Function**

     - In the search bar look for **Lambda**, It should take we to the _Lambda begin page_

     ![Lambda](../../../images/3/3.1/3.1.2/Lambda.png?width=90pc)

     - Click **Create a function**

     ![Lambda](../../../images/3/3.1/3.1.2/Create_function.png?width=90pc)

     - Name the function : `ec2instance-containment-with-forensics`.
     - Select the Runtime as : **Python 3.9**.
     - Expand the _Change default execution role_, choose **Use a existing role**.
     - Select the `ec2instance-containment-with-forensics-role` as execution role.
     - The result should be like this, then click **Create function**
     
     ![Lambda](../../../images/3/3.1/3.1.2/Create_function_settings.png?width=90pc)

2. Modify the prior created **Lambda function**
     - Click the _Configuration_, then click the _Edit_ button.
     
     ![Lambda](../../../images/3/3.1/3.1.2/Configure_function_runtime1.png?width=90pc)

     - Change the **Timeout** to 15 min, then save.

     ![Lambda](../../../images/3/3.1/3.1.2/Configure_function_runtime2.png?width=90pc)
       
     - Now we will create the **environment variables** to the **lambda function**
     - Still in the _Configuration_, select the **Environment variables** and click _Edit_.

     ![Lambda](../../../images/3/3.1/3.1.2/Configure_function_create_env_var.png?width=90pc)

     - Select **Add environment variable**.
       - Key: `ForensicsSG`
       - Value: `sg-...(the ID of your Forensics SG)`
     - They should be like as below.

     ![Lambda](../../../images/3/3.1/3.1.2/Configure_function_add_env_var.png?width=90pc)

     - Then click **Save**. 

3. Add the code for the **Lambda Function**
     - Click the _Code_ next to the _Configuration_.
     
     ![Lambda](../../../images/3/3.1/3.1.2/Add_code_Lambda.png?width=90pc)
     
     - In the code editor, paste the _following code_.
     
     ```python
          import boto3, json
          import time
          from datetime import date
          from botocore.exceptions import ClientError
          import os

          def lambda_handler(event, context):
          # Copyright 2022 - Amazon Web Services

          # Permission is hereby granted, free of charge, to any person obtaining a copy of this
          # software and associated documentation files (the "Software"), to deal in the Software
          # without restriction, including without limitation the rights to use, copy, modify,
          # merge, publish, distribute, sublicense, and/or sell copies of the Software, and to
          # permit persons to whom the Software is furnished to do so.

          # THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
          # INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A
          # PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
          # HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
          # OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
          # SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

          # print('## ENVIRONMENT VARIABLES')
          # print(os.environ)
          # print('## EVENT')
          # print(event)
          response = 'Error remediating the security finding.'
          try:
               # Gather Instance ID from CloudWatch event
               instanceID = event['detail']['resource']['instanceDetails']['instanceId']
               print('## INSTANCE ID: %s' % (instanceID))
               
               # Get instance details
               client = boto3.client('ec2')
               ec2 = boto3.resource('ec2')
               instance = ec2.Instance(instanceID)
               instance_description = client.describe_instances(InstanceIds=[instanceID])
               print('## INSTANCE DESCRIPTION: %s' % (instance_description))

               #-------------------------------------------------------------------
               # Protect instance from termination
               #-------------------------------------------------------------------
               ec2.Instance(instanceID).modify_attribute(
               DisableApiTermination={
                    'Value': True
               })
               ec2.Instance(instanceID).modify_attribute(
               InstanceInitiatedShutdownBehavior={
                    'Value': 'stop'
               })
               
               #-------------------------------------------------------------------
               # Create tags to avoid accidental deletion of forensics evidence
               #-------------------------------------------------------------------
               ec2.create_tags(Resources=[instanceID], Tags=[{'Key':'status', 'Value':'isolated'}])
               print('## INSTANCE TAGS: %s' % (instance.tags))

               #------------------------------------
               ## Isolate Instance
               #------------------------------------
               print('quarantining instance -- %s, %s' % (instance.id, instance.instance_type))
               
               # Change instance Security Group attribute to terminate connections and allow Forensics Team's access
               instance.modify_attribute(Groups=[os.environ['ForensicsSG']])
               print('Instance ready for root cause analysis -- %s, %s' % (instance.id,  instance.security_groups))

               #------------------------------------
               ## Create snapshots of EBS volumes 
               #------------------------------------
               description= 'Isolated Instance:' + instance.id + ' on account: ' + event['detail']['accountId'] + ' on ' + date.today().strftime("%Y-%m-%d  %H:%M:%S")
               SnapShotDetails = client.create_snapshots(
                    Description=description,
                    InstanceSpecification = {
                         'InstanceId': instanceID,
                         'ExcludeBootVolume': False
                    }
               )
               print('Snapshot Created -- %s' % (SnapShotDetails))

               response = 'Instance ' + instance.id + ' auto-remediated'        
               
          except ClientError as e:
               print(e)
          
          return response

    ```

     - Then click on **deploy**, as shown below.
     
     ![Lambda](../../../images/3/3.1/3.1.2/Deploy_code_Lambda.png?width=90pc)

{{% notice note %}}
You can review comments on the code to understand what it's doing.
{{% /notice %}}

If you done with that, the next step which we will [Test the Lambda Function](../3.1.3-Test-Lambda-Function).

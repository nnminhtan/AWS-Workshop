+++
title = "Tạo Lambda Function"
date = 2025
weight = 2
chapter = false
pre = "<b>3.1.2. </b>"
+++

<!-- #### Create Lambda Function -->

1. Tạo **Lambda Function**

   - Trong thanh tìm kiếm, nhập **Lambda**, bạn sẽ được chuyển tới trang bắt đầu của Lambda.

   ![Lambda](../../../../images/3/3.1/3.1.2/Lambda.png?width=90pc)

   - Nhấn **Create a function**

   ![Lambda](../../../../images/3/3.1/3.1.2/Create_function.png?width=90pc)

   - Đặt tên function là: `ec2instance-containment-with-forensics`.
   - Chọn Runtime: **Python 3.9**.
   - Mở rộng phần _Change default execution role_, chọn **Use an existing role**.
   - Chọn role `ec2instance-containment-with-forensics-role`.
   - Kết quả sẽ như bên dưới, nhấn **Create function**.

   ![Lambda](../../../../images/3/3.1/3.1.2/Create_function_settings.png?width=90pc)

2. Sửa đổi **Lambda function** đã tạo

   - Vào tab _Configuration_, bấm nút _Edit_.

   ![Lambda](../../../../images/3/3.1/3.1.2/Configure_function_runtime1.png?width=90pc)

   - Thay đổi **Timeout** thành 15 phút, rồi lưu lại.

   ![Lambda](../../../../images/3/3.1/3.1.2/Configure_function_runtime2.png?width=90pc)

   - Tạo **environment variables** cho Lambda function.
   - Vẫn trong _Configuration_, chọn **Environment variables** rồi bấm _Edit_.

   ![Lambda](../../../../images/3/3.1/3.1.2/Configure_function_create_env_var.png?width=90pc)

   - Thêm biến môi trường:
     - Key: `ForensicsSG`
     - Value: `sg-...(ID của Security Group Forensics của bạn)`
   - Kết quả như hình bên dưới.

   ![Lambda](../../../../images/3/3.1/3.1.2/Configure_function_add_env_var.png?width=90pc)

   - Nhấn **Save**.

3. Thêm code cho **Lambda Function**

   - Chọn tab _Code_ bên cạnh _Configuration_.

   ![Lambda](../../../../images/3/3.1/3.1.2/Add_code_Lambda.png?width=90pc)

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

   - Nhấn **Deploy** để deploy function Lambda.

   ![Lambda](../../../../images/3/3.1/3.1.2/Deploy_code_Lambda.png?width=90pc)

{{% notice note %}}
Bạn có thể xem các comment trong code để hiểu chức năng từng phần.
{{% /notice %}}

Sau khi hoàn thành, tiếp tục với bước [Test Lambda Function](../3.1.3-Test-Lambda-Function).

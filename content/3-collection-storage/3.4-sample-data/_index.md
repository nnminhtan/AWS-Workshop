+++
title = "Create Sample Data"
date = 2020
weight = 4
chapter = false
pre = "<b>3.4. </b>"
+++

## Create Sample Data

1.  Access [amazon-kinesis-data-generator-link](https://awslabs.github.io/amazon-kinesis-data-generator/web/producer.html), the following interface will be displayed:

- Click on **Help**.

![Generate](/images/3/3.4/data_generate.png?width=90pc)

- Select **Create a Cognito User with CloudFormation**.

![Generate](/images/3/3.4/create_w_cloudformation.png?width=90pc)

- This will take you to the **Create stack** interface.

{{% notice note %}}
Note: Switch to the Singapore region (ap-southeast-1).
{{% /notice %}}
![Generate](/images/3/3.4/change_region.png?width=90pc)

- Review the configurations and select **Next**.

![Generate](/images/3/3.4/create_stack.png?width=90pc)

2.  In the **Specify stack details** step:

- Enter **Stack name** as `Kinesis-Data-Generator-Cognito-User`.
- In the **Parameters** section:
  - **Username**: Enter `admin`.
  - **Password**: Enter the password you want to set.

{{% notice note %}}
Note: According to the CloudFormation template being used, the password must be at least 6 characters long, including both letters and numbers, and contain at least one number.
{{% /notice %}}
![Generate](/images/3/3.4/username_pwd.png?width=90pc)

3.  In the **Configure stack options** step:

- Leave the default values.
- Select **I acknowledge that AWS CloudFormation might create IAM resources.**
- Select **Next**.

  ![Generate](/images/3/3.4/submit_stack.png?width=90pc)

4.  In the **Review and create** step:

- Review the stack details.
- Then, select **Submit**.

  ![Generate](/images/3/3.4/review_stack.png?width=90pc)
  ![Generate](/images/3/3.4/review_submit_stack.png?width=90pc)

5. Wait for the stack creation process to complete.

6. Once successfully created, check the **Output** section.

   ![Generate](/images/3/3.4/output_stack.png?width=90pc)

7. Click on the link in the **Output** section, which will redirect you to the **Amazon Kinesis Data Generator** interface. Log in using the **username** and **password** created in the previous stack.

   ![Generate](/images/3/3.4/signin_generate.png?width=90pc)

8. Setup the following values:

- **Region**: **ap-southeast-1**.
- **Stream/delivery stream**: **FCJ-FirehoseStream**.
- **Records per second**: `2000`.

  ![Generate](/images/3/3.4/generate_para.png?width=90pc)

- **Record template**: **Template 1**.
- Enter the following in **Template 1**:

```
{
  "uuid": "{{random.uuid}}",
  "device_ts": "{{date.utc("YYYY-MM-DD HH:mm:ss.SSS")}}",
  "device_id": {{random.number(50)}},
  "device_temp": {{random.weightedArrayElement(
    {"weights":[0.30, 0.30, 0.20, 0.20],"data":[32, 34, 28, 40]}
  )}},
  "track_id": {{random.number(30)}},
  "activity_type": {{random.weightedArrayElement(
        {
            "weights": [0.1, 0.2, 0.2, 0.3, 0.2],
            "data": ["\"Running\"", "\"Working\"", "\"Walking\"", "\"Traveling\"", "\"Sitting\""]
        }
    )}}
}

```

- Select **Send**.

![Generate](/images/3/3.4/generate_para_2.png?width=90pc)

9. Wait for the generation process to complete and send about **100,000** records, then select **Stop Sending Data to Kinesis**.

   ![Generate](/images/3/3.4/stop_generate.png?width=90pc)

10. Find and select **S3**. Check if the generated data has been sent to **S3**.

    ![Generate](/images/3/s3.png?width=90pc)

11. Verify the data has been successfully sent to **S3**.

    ![Generate](/images/3/3.4/check_data_inS3.png?width=90pc)

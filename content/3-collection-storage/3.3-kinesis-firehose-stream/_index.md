+++
title = "Create Firehose Stream"
date = 2020
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++

## Create Firehose Stream

1. Search for and select the **Kinesis** service.

   ![Kinesis](/images/3/3.3/kinesis.png?width=90pc)

2. Select **Amazon Data Firehose**.

   ![Kinesis](/images/3/3.3/choose_data_firehose.png?width=90pc)

3. Click **Create Firehose Stream**.

   ![Kinesis](/images/3/3.3/create_firehosestr_button.png?width=90pc)

4. In the **Create Firehose Stream** interface:

   - For **Source**, choose **Direct PUT**.
   - For **Destination**, choose **Amazon S3**.
   - For **Firehose stream name**, enter `FCJ-FirehoseStream`.

   ![Kinesis](/images/3/3.3/firehose_parameters.png?width=90pc)

   - Review the values in **Transform and convert records**.

   ![Kinesis](/images/3/3.3/firehose_transform_convert.png?width=90pc)

   - In **Destination Settings**:

     - Click **Browse**.
       ![Kinesis](/images/3/3.3/firehose_browse_s3_btn.png?width=90pc)
     - Select the **asg-datalake-demo-2024** bucket.
     - Click **Create**.

       ![Kinesis](/images/3/3.3/firehose_choose_s3_bucket.png?width=90pc)

     - Verify the settings.
       ![Kinesis](/images/3/3.3/destination_setting_1.png?width=90pc)
     - In **S3 bucket prefix**, enter `data/raw`.
     - In **S3 bucket error output prefix**, enter `data/error`.

       ![Kinesis](/images/3/3.3/destination_setting_2.png?width=90pc)

     - Click **Create Firehose stream**.

       ![Kinesis](/images/3/3.3/create_firehose_submit.png?width=90pc)

   - The Firehose stream was created successfully.

     ![Kinesis](/images/3/3.3/succes_create_firehose.png?width=90pc)

+++
title = "Tạo Firehose Stream"
date = 2020
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++

## Tạo Firehose Stream

1. Tìm kiếm và chọn dịch vụ **Kinesis**

   ![Kinesis](/images/3/3.3/kinesis.png?width=90pc)

2. Chọn **Amazon Data Firehose**

   ![Kinesis](/images/3/3.3/choose_data_firehose.png?width=90pc)

3. Chọn **Create Firehose Stream**

   ![Kinesis](/images/3/3.3/create_firehosestr_button.png?width=90pc)

4. Tại giao diện **Create Firehose Stream**

   - Tại **Source** chọn **Direct PUT**
   - Tại **Destination** chọn **Amazon S3**
   - Tại **Firehose stream name** đặt tên `FCJ-FirehoseStream`

   ![Kinesis](/images/3/3.3/firehose_parameters.png?width=90pc)

   - Kiểm tra các giá trị ở **Transform and convert records**

   ![Kinesis](/images/3/3.3/firehose_transform_convert.png?width=90pc)

   - Ở **Destination Setting**

     - Chọn **Browse**
       ![Kinesis](/images/3/3.3/firehose_browse_s3_btn.png?width=90pc)
     - Chọn bucket **asg-datalake-demo-2024**
     - Chọn **Create**

       ![Kinesis](/images/3/3.3/firehose_choose_s3_bucket.png?width=90pc)

     - Kiểm tra
       ![Kinesis](/images/3/3.3/destination_setting_1.png?width=90pc)
     - Ở **S3 bucket prefix**, nhập `data/raw`
     - Ở **S3 bucket error output prefix**, nhập `data/error`

       ![Kinesis](/images/3/3.3/destination_setting_2.png?width=90pc)

     - Chọn **Create Firehose stream**

       ![Kinesis](/images/3/3.3/create_firehose_submit.png?width=90pc)

   - Tạo Firehose stream thành công
     ![Kinesis](/images/3/3.3/succes_create_firehose.png?width=90pc)

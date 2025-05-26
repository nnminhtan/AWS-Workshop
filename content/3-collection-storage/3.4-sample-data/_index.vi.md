+++
title = "Tạo dữ liệu mẫu"
date = 2020
weight = 4
chapter = false
pre = "<b>3.4. </b>"
+++

## Tạo dữ liệu mẫu

1.  Truy cập vào [amazon-kinesis-data-generator-link](https://awslabs.github.io/amazon-kinesis-data-generator/web/producer.html), sẽ hiển thị giao diện sau:

- Click vào **Help**

![Generate](/images/3/3.4/data_generate.png?width=90pc)

- Chọn **Create a Cognito User with CloudFormation**

![Generate](/images/3/3.4/create_w_cloudformation.png?width=90pc)

- Sau đó, sẽ dẫn đến giao diện **Create stack**

{{% notice note %}}
Lưu ý chuyển sang region Singapore (ap-southeast-1).
{{% /notice %}}
![Generate](/images/3/3.4/change_region.png?width=90pc)

- Kiểm tra các cấu hình, sau đó chọn **Next**

![Generate](/images/3/3.4/create_stack.png?width=90pc)

2. Ở bước **Specify stack details**

- **Stack name**, nhập `Kinesis-Data-Generator-Cognito-User`
- Trong phần **Parameters**:
  - **Username**: Nhập `admin`
  - **Password**: Nhập password bạn muốn đặt

{{% notice note %}}
Lưu ý theo như template của CloudFormation mà ta đang dùng, password phải có ít nhất 6 ký tự gồm chữ và số, trong đó chứa ít nhất một số
{{% /notice %}}
![Generate](/images/3/3.4/username_pwd.png?width=90pc)

3. Ở bước **Configure stack options**

- Để nguyên các giá trị mặc định
- Chọn **I acknowledge that AWS CloudFormation might create IAM resources.**
- Chọn **Next**
  ![Generate](/images/3/3.4/submit_stack.png?width=90pc)

4. Ở bước **Review and create**

- Kiểm tra lại stack
- Sau đó chọn **Submit**

  ![Generate](/images/3/3.4/review_stack.png?width=90pc)
  ![Generate](/images/3/3.4/review_submit_stack.png?width=90pc)

5. Đợi quá trình Stack được tạo

6. Sau khi tạo thành công, kiểm tra phần **Output**
   ![Generate](/images/3/3.4/output_stack.png?width=90pc)

7. Click vào đường link ở phần **Output**, ta được dẫn đến giao diện **Amazon Kinesis Data Generator**. Ta tiến hành đăng nhập với thông tin **username** và **password** đã tạo ở stack trước đó

   ![Generate](/images/3/3.4/signin_generate.png?width=90pc)

8. Setup các giá trị sau:

- **Region**: **ap-southeast-1**
- **Stream/delivery stream**: **FCJ-FirehoseStream**
- **Records per second**: `2000`
  ![Generate](/images/3/3.4/generate_para.png?width=90pc)
- **Record template**: **Template 1**
- Nhập vào Template 1:

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

- Chọn **Send**

![Generate](/images/3/3.4/generate_para_2.png?width=90pc)

9. Đợi quá trình generate cho tới khi nhận được khoảng **100.000** records thì chọn **Stop Sending Data to Kinesis**
   ![Generate](/images/3/3.4/stop_generate.png?width=90pc)

10. Tìm và chọn **S3**. Ta kiểm tra xem dữ liệu vừa generate đã đi tới **S3** hay chưa.
    ![Generate](/images/3/s3.png?width=90pc)

11. Kiểm tra dữ liệu đã đi tới **S3** thành công
    ![Generate](/images/3/3.4/check_data_inS3.png?width=90pc)

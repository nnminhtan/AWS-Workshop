+++
title = "Tạo Glue Crawler"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++

## Tạo Glue Crawler

1. Tìm và chọn **AWS Glue**

   ![Glue](/images/4/4.1/glue_service.png?width=90pc)

2. Trong giao diện **AWS Glue**

- Chọn **Crawler**
- Chọn **Create crawler**
  ![Glue](/images/4/4.1/btn_create_cwl.png?width=90pc)

3. Trong giao diện **Add new crawler**

- Ở bước **Set crawler properties**

  - Nhập **Name** là `summitcrawler`
  - Chọn **Next**

  ![Glue](/images/4/4.1/cwl_properties.png?width=90pc)

- Ở bước **Choose data sources and classifiers**

  - Chọn **Add a data source**

  ![Glue](/images/4/4.1/add_data_source.png?width=90pc)

  - Chọn **Data source S3**
  - Chọn **Browse S3**
  - Chọn **S3 path** (như hình ảnh)
  - Chọn **Crawler new sub-folders only**
  - Chọn **Add an S3 data source**

  ![Glue](/images/4/4.1/add_data_src_form.png?width=90pc)

  - Sau đó chọn **Next**
    ![Glue](/images/4/4.1/next_step2.png?width=90pc)

- Ở bước **Configure security settings**

  - Chọn **IAM role**: **AWSGlueServiceRoleDefault**
  - Chọn **Next**
    ![Glue](/images/4/4.1/next_step3.png?width=90pc)

- Ở bước **Set output and scheduling**

  - Chọn **Add database**
    ![Glue](/images/4/4.1/step4_add_db.png?width=90pc)

  - Ở giao diện **Create database**:
    - Đặt tên database: `summitdb`
    - Chọn **Create database**
      ![Glue](/images/4/4.1/create_db.png?width=90pc)
  - Quay lại giao diện bước **Set output and scheduling**
    - Chọn **target database**: `summitdb`
    - Chọn **Next**

{{% notice note %}}
Nếu **summitdb** không hiển thị, bạn có thể bấm button reload bên cạnh textfield **Target database**
{{% /notice %}}

![Glue](/images/4/4.1/next_step4.png?width=90pc)

- Ở bước **Review and create**

  - Review lại các cấu hình
  - Chọn **Create crawler**

![Glue](/images/4/4.1/review_create_cwl.png?width=90pc)

4. Sau khi tạo crawler thành công, chọn **Run crawler**

![Glue](/images/4/4.1/run_cwl.png?width=90pc)

5. Đợi một khoảng thời gian để crawler run. Sau khi run thành công, crawler ở trạng thái **Complete**

![Glue](/images/4/4.1/complete_run_swl.png?width=90pc)

6. Chọn **Tables** ở giao diện **AWS Glue**, chúng ta sẽ thấy có 2 bảng dữ liệu.

![Glue](/images/4/4.1/check_data_in_table_after_run.png?width=90pc)

7. Dữ liệu ở **raw2024**

![Glue](/images/4/4.1/at_raw2024.png?width=90pc)

8. Dữ liệu ở **reference_data**

![Glue](/images/4/4.1/at_ref_data.png?width=90pc)

+++
title = "Visualize với QuickSight"
date = 2020
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++

## Visualize với QuickSight

Chúng ta sẽ dùng **QuickSight** để trực quan hóa dữ liệu từ table **processed_data**

Trước tiên, ta sẽ tạo tài khoản **Quicksight**

{{% notice info %}}
Nếu bạn đã có tài khoản **QuickSight** thì có thể bỏ qua bước này
{{% /notice %}}

### Tạo tài khoản QuickSight

1. Tìm kiếm và chọn dịch vụ **QuickSight**

![QuickSight](/images/6/6.2/quicksight.png?width=90pc)

2. Sign up for **QuickSight**

![QuickSight](/images/6/6.2/signup_ud.png?width=90pc)

3. Nhập **email** của bạn, chọn **Authentication Method** và chọn region **Asia Pacific (Singapore)**

![QuickSight](/images/6/6.2/quicksight_form_ud.png?width=90pc)

4. Ở **Account info**

- Nhập `demo-visualize` làm **QuickSight account name**
- IAM role: chọn **Use QuickSight-managed role (default)**

![QuickSight](/images/6/6.2/quicksight_form2.png?width=90pc)

- Chọn **Finish**

![QuickSight](/images/6/6.2/fiinish_signup.png?width=90pc)

- Sau khi đăng ký thành công, ta vào được giao diện **QuickSight**

![QuickSight](/images/6/6.2/quicksight_dashboard.png?width=90pc)

### Thực hiện trực quan hóa dữ liệu

1. Tại giao diện **QuickSight**, chọn **Manage QuickSight**

![QuickSight](/images/6/6.2/manage_quicksight.png?width=90pc)

2. Chọn **Security & permissions**, chọn **Manage**

![QuickSight](/images/6/6.2/click_manage_setting.png?width=90pc)

3. Tick chọn các service

- Đối với **Amazon S3**: chọn **S3 Buckets Linked To QuickSight Account**, chọn bucket **asg-datalake-demo-2024**, sau đó chọn **Finish**

![QuickSight](/images/6/6.2/allow_s3.png?width=90pc)

4. Tick chọn các dịch vụ còn lại, sau đó chọn **Save**

![QuickSight](/images/6/6.2/save_allow.png?width=90pc)

5. Trở lại giao diện **QuickSight**

- Chọn **Dataset**
- Chọn **New dataset**

![QuickSight](/images/6/6.2/create_dataset_btn_ud.png?width=90pc)

6. Tạo **data source**

- Chọn **Athena**
- Nhập **Data source name** là `summitdemo`
- Chọn **Validate Connection**. Nếu kết nối thành công, sẽ hiển thị **SSL is enabled**
- Chọn **Create data source**

![QuickSight](/images/6/6.2/create_data_source.png?width=90pc)

7. Chọn **Table**:

- **Catalog**, chọn **AwsDataCatalog**
- **Database**, nhập `summitdb`
- **Table**, chọn **processed_data**
- Chọn **Select**

![QuickSight](/images/6/6.2/select_table.png?width=90pc)

8. Trong bước **Finish dataset creation**:

- Chọn **Directly query your data**
- Chọn **Visualize**

![QuickSight](/images/6/6.2/finish_create_dataset.png?width=90pc)

9. Sử dụng **Amazon Quick Sight** để visualize các dữ liệu đã được chuyển đổi (transform):

- Tạo 1 **Tree map** của users và số tracks nhạc mà họ nghe.
- Click vào chọn **Tree Map**

![QuickSight](/images/6/6.2/tree_map.png?width=90pc)

- Kết quả **Tree map**

![QuickSight](/images/6/6.2/treemap.png?width=90pc)

10. Ta có thể sử dung với các **Visual types** khác, chẳng hạn **Pie chart**

![QuickSight](/images/6/6.2/piechart.png?width=90pc)

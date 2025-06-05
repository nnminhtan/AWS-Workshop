+++
title = "Tạo object cho S3 bucket"
date = 2020
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

## Tạo object cho S3 bucket

1. Tiếp theo, click vào bucket vừa tạo. Tại tab **Object** chọn **Create folder**

   ![object](/images/3/create_folder_s3.png?width=90pc)

2. Trong giao diện **Create bucket**, đặt **Folder name** là `data`

   ![object](/images/3/name_folder_data.png?width=90pc)

3. Kiểm tra các cấu hình và chọn **Create folder**

   ![object](/images/3/name_folder_data_and_submit.png?width=90pc)

4. Tương tự với cách tạo folder, ta sẽ tạo folder `reference_data` ở trong folder **data**

   ![object](/images/3/create_ref_data_folder.png?width=90pc)
   ![object](/images/3/create_ref_data_folder_submit.png?width=90pc)

5. Tạo folder **reference_data** thành công

   ![object](/images/3/create_ref_data_folder_success.png?width=90pc)

6. Tiến hành download file **tracks_list.json** [tại đây](https://raw.githubusercontent.com/ngcuyen/ws-doc/refs/heads/main/tracks_list.json)

   - **Ctrl + S** để lưu file

7. Tiến hành upload file **tracks_list.json** lên folder **reference_data**

   - Chọn **Object**
   - Chọn **Upload**
     ![object](/images/3/upload_tracklist.png?width=90pc)
   - Chọn **Add file**, chọn file đã tải
   - Chọn file **tracks_list.json**
     ![object](/images/3/add_file_tracklist.png?width=90pc)
   - Chọn **Upload**
     ![object](/images/3/upload_submit.png?width=90pc)
   - Upload file thành công
     ![object](/images/3/upload_success.png?width=90pc)

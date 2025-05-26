+++
title = "Create Glue Crawler"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++

## Create Glue Crawler

1. Search and select **AWS Glue**

   ![Glue](/images/4/4.1/glue_service.png?width=90pc)

2. In the **AWS Glue** interface

- Select **Crawler**
- Click **Create crawler**
  ![Glue](/images/4/4.1/btn_create_cwl.png?width=90pc)

3. In the **Add new crawler** interface

- In the **Set crawler properties** step

  - Enter **Name** as `summitcrawler`
  - Click **Next**

  ![Glue](/images/4/4.1/cwl_properties.png?width=90pc)

- In the **Choose data sources and classifiers** step

  - Click **Add a data source**

  ![Glue](/images/4/4.1/add_data_source.png?width=90pc)

  - Select **Data source S3**
  - Click **Browse S3**
  - Select **S3 path** (as shown in the image)
  - Choose **Crawler new sub-folders only**
  - Click **Add an S3 data source**

  ![Glue](/images/4/4.1/add_data_src_form.png?width=90pc)

  - Then click **Next**
    ![Glue](/images/4/4.1/next_step2.png?width=90pc)

- In the **Configure security settings** step

  - Choose **IAM role**: **AWSGlueServiceRoleDefault**
  - Click **Next**
    ![Glue](/images/4/4.1/next_step3.png?width=90pc)

- In the **Set output and scheduling** step

  - Click **Add database**
    ![Glue](/images/4/4.1/step4_add_db.png?width=90pc)

  - In the **Create database** interface:
    - Name the database: `summitdb`
    - Click **Create database**
      ![Glue](/images/4/4.1/create_db.png?width=90pc)
  - Return to the **Set output and scheduling** interface
    - Select **target database**: `summitdb`
    - Click **Next**

{{% notice note %}}
If **summitdb** does not appear, click the reload button next to the **Target database** text field.
{{% /notice %}}

![Glue](/images/4/4.1/next_step4.png?width=90pc)

- In the **Review and create** step

  - Review the configurations
  - Click **Create crawler**

![Glue](/images/4/4.1/review_create_cwl.png?width=90pc)

4. After successfully creating the crawler, click **Run crawler**

![Glue](/images/4/4.1/run_cwl.png?width=90pc)

5. Wait for the crawler to run. Once it completes, the crawler will be in **Complete** status

![Glue](/images/4/4.1/complete_run_swl.png?width=90pc)

6. Select **Tables** in the **AWS Glue** interface, we will see 2 data tables.

![Glue](/images/4/4.1/check_data_in_table_after_run.png?width=90pc)

7. Data in **raw2024**

![Glue](/images/4/4.1/at_raw2024.png?width=90pc)

8. Data in **reference_data**

![Glue](/images/4/4.1/at_ref_data.png?width=90pc)

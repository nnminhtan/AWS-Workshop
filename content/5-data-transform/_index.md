+++
title = "Data Transformation"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

### Data Transformation

1. Search for and select the **Glue** service

![Glue](/images/5/glue.png?width=90pc)

2. Select **Notebook**

![Glue](/images/5/create_notebook_btn.png?width=90pc)

3. Download the file [notebook.ipynb](https://github.com/ngcuyen/ws-doc/blob/main/notebook.ipynb)

4. In the **Notebook** form:

- Select **Upload Notebook**
- Choose **Choose file**
- Select the downloaded notebook file
- IAM role: select **AWSGlueServiceRoleDefault**
- Select **Create notebook**

![Glue](/images/5/upload_notebook.png?width=90pc)

5. Wait for the **notebook** to start, then run each **cell** of the notebook and view the results

- First, run the cell to create the session

![Glue](/images/5/nb1.png?width=90pc)

- Session initialized successfully

![Glue](/images/5/nb1.1.png?width=90pc)

- Go to **Interactive Session**, check and see the session has been successfully created

![Glue](/images/5/session_created.png?width=90pc)

- In cell [2]: Import **SparkContext, GlueContext, boto3, awsglue**, and initialize the session
- In cell [3]: The **GlueContext** initialization command is used to access **ETL** features of **AWS Glue** and retrieve **SparkSession** for data processing with **Apache Spark**.

![Glue](/images/5/nb23.png?width=90pc)

- In cell [4]: Create two **DynamicFrames** **raw_data** and **reference_data** by retrieving data from the **raw2024** and **reference_data** tables in the **summitdb** database in the **AWS Glue Data Catalog**.
- In cell [5]: The command `raw_data.printSchema()` displays the schema of the **DynamicFrame** **raw_data**, including the columns, data types, and nested structures (if any).

![Glue](/images/5/nb45.png?width=90pc)

- In cell [6]: The command `reference_data.printSchema()` displays the schema of the **DynamicFrame** **reference_data**, including the columns and corresponding data types.
- In cell [7]: These commands display the number of records in both **DynamicFrames** **raw_data** and **reference_data**.

![Glue](/images/5/nb67.png?width=90pc)

- In cell [8]: View the first 5 records in **raw_data** as a **Spark DataFrame**.

![Glue](/images/5/nb8.png?width=90pc)

- In cell [9]: View the first 5 records in **reference_data** as a **Spark DataFrame**.

![Glue](/images/5/nb9.png?width=90pc)

- In cell [10]: Create a temporary table from **raw_data**, query records with **activity_type** equal to "**Running**" and display the count and the first 5 records of the result.

![Glue](/images/5/nb10.png?width=90pc)

- In cell [11]: Query records with **activity_type** equal to "**Working**" from the temporary table **temp_raw_data**, display the count and the first 5 records.

![Glue](/images/5/nb11.png?width=90pc)

- In cell [12]: Apply a filter to keep only the records with **activity_type** equal to "**Running**" from **raw_data**, then count these records.

![Glue](/images/5/nb12.png?width=90pc)

- In cell [13]: Keep only the records with **activity_type** equal to "**Working**" from **raw_data**, then display the count of these records.
- In cell [14]: Perform a join between **raw_data** and **reference_data** based on the **track_id** field, creating a new **DynamicFrame** called **joined_data**

![Glue](/images/5/nb1314.png?width=90pc)

- In cell [15]: View an overview of the fields and data types after the two **DynamicFrames** are joined.

![Glue](/images/5/nb15.png?width=90pc)

- In cell [16]: Remove unnecessary fields (**partition_0, partition_1, partition_2, partition_3**) from **joined_data** and store the result in **joined_data_clean**

![Glue](/images/5/nb16.png?width=90pc)

- In cell [17]: Display the schema of **joined_data_clean** after cleaning the data by removing unwanted fields.

![Glue](/images/5/nb17.png?width=90pc)

- In cell [18]: View the first 5 records in **joined_data_clean** as a **Spark DataFrame**.

![Glue](/images/5/nb18.png?width=90pc)

- In cell [19]: Write the data from **joined_data_clean** to S3 in Parquet format, and if an error occurs during the write, print the error message.

![Glue](/images/5/nb19.png?width=90pc)

- In cell [20]: Use **Boto3** to trigger **summitcrawler**, then check the crawler status in a loop until it stops. When the crawler stops, print a message and exit.

![Glue](/images/5/nb20.png?width=90pc)

- In cell [21]: Use the **AWS Glue client** to retrieve a list of tables in the **summitdb** database and print the name of each table.

![Glue](/images/5/nb21.png?width=90pc)

6. Check if the data has been loaded into **S3**, search for and select the **S3** service

![S3](/images/3/s3.png?width=90pc)

7. Check in **asg-datalake-demo-2024/data**

![S3](/images/5/processdata_ins3.png?width=90pc)

8. Check the objects in **processed-data**

![S3](/images/5/object_in_processdata.png?width=90pc)

+++
title = "Introduction"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

# Understanding Data Lake on AWS

#### Introduction to Data Lake

**Data Lake** is a centralized storage system that allows storing data in any format—structured, semi-structured, or unstructured. Unlike traditional databases requiring data formatting before storage, Data Lake stores raw data and processes or analyzes it when needed.

#### Benefits of Data Lake

- **Flexible Storage**: Supports data from various sources and formats.

- **Comprehensive Analysis**: Enables big data analysis and AI/ML applications.

- **Cost Efficiency**: Utilizes low-cost storage solutions like Amazon S3.

- **Seamless Integration**: Connects smoothly with analysis and reporting tools like Amazon Athena and QuickSight.

#### Challenges of Data Lake Implementation

- **Data Management**: How to organize and manage data efficiently?

- **Security**: How to prevent unauthorized access to data?

- **Scalability**: The system must scale to handle data growth.

- **Performance**: Optimization is needed for querying and data processing.

- **Data Quality**: Ensuring data accuracy and reliability is crucial.

#### Workshop Architecture

##### Architecture Overview

The diagram below illustrates the Data Lake system architecture we will deploy in this workshop:
![Workshop](/images/1/workshop.jpg)

##### Architecture Description

- **Data Collection**:

  - Data from various sources is collected through Kinesis.
  - Kinesis Firehose Stream processes and transfers data to Amazon S3.

- **Raw Data Storage**:

  - Raw data is stored in S3 under the "raw data" folder.
  - CloudFormation automatically deploys required resources.

- **AWS Glue**:

  - AWS Glue Crawler scans raw data in S3 to create metadata.
  - Metadata is stored in the AWS Glue Data Catalog.
  - An ETL Job (Extract, Transform, Load) processes and transforms raw data.

- **Processed Data Storage**:

  - Transformed data is stored in another S3 bucket under the "processed-data" folder.

- **Data Analysis and Visualization**:

  - AWS Glue Crawler scans processed data and updates the Glue Data Catalog.
  - Amazon Athena queries data in S3.
  - Amazon QuickSight connects to the data for visualization and reporting.

##### Workshop Objectives

- Understand the components of the Data Lake architecture.
- Deploy a simple Data Lake system using AWS services.
- Integrate analysis and visualization tools to extract useful insights from the data.

{{% notice info %}}
This lab is conducted in the Singapore region (ap-southeast-1).
{{% /notice %}}

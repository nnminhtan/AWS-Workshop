+++
title = "Analysis and Visualization"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

## Amazon Athena

**Amazon Athena** is an interactive query service used for analyzing data in Amazon S3 using standard SQL. We just need to point to your data in Amazon S3, define the schema, and start querying using the integrated query editor. Amazon Athena allows us to analyze all of our data in Amazon S3 without needing to set up complex ETL processes. Amazon Athena charges based on the amount of queries run.

**Amazon Athena** uses Presto with ANSI SQL support and works with many standard data formats, including CSV, JSON, ORC, Avro, and Parquet. Athena is recommended for quick query needs but is also capable of handling complex analysis, including joins on large datasets, window functions, and arrays.

## Amazon QuickSight

**Amazon QuickSight** is a fully managed data visualization service provided by AWS.

- **Data source** is an external data repository, and you need to configure access to the data in this external data store, such as Amazon S3, Amazon Athena, Salesforce, etc.

- **Dataset** defines the specific data within the Data source that you want to use. For example, the Data source could be a table if you are connecting to a database. It could be a file if you are connecting to Amazon S3.

- **Analysis** is where a set of visuals and related stories are kept, such as all stories applying to a certain business objective or KPI.

- **Visual** is a graphical representation of your data. You can create different types of visuals in an analysis using different datasets and visual types.

- **Dashboard** is a page that contains one or more analyses for viewing purposes, which you can share with other Amazon QuickSight users for reporting. The dashboard retains the configuration of the analysis at the time you publish it, including elements such as filters, parameters, controls, and sorting order.

## Contents:

1. [Analysis with Athena](6.1-athena)
2. [Visualize with QuickSight](6.2-quicksight)

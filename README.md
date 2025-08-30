# FlowForge-AWS_Pipeline
FlowForge is a real-time data pipeline using AWS Kinesis, Lambda, EMR, Databricks, Glue, Athena, and Airflow. It transforms streaming data, stores results in Delta Lake, and sends alerts with SNS—enabling fast, reliable data processing and orchestration at scale.

<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/54921f2d-73a6-4929-9695-34c8c5d29d2b" />
# Retail Store Real-Time Data Processing Pipeline

## 🚀 Project Architecture Overview

---

### 1. Input Data  
The journey begins with **transactional data in JSON format** from retail stores supplying detailed records.

---

### 2. Amazon Kinesis Data Streams  
<img src="https://cdn.worldvectorlogo.com/logos/amazon-kinesis-1.svg" alt="Kinesis Logo" width="100"/>
Amazon Kinesis Data Streams (KDS) is a fully managed service that collects and processes real-time streaming data at scale.  
In this project, it ingests live transactional data for immediate downstream processing.

---

### 3. AWS Lambda Processor  
<img src="https://cdn.worldvectorlogo.com/logos/aws-lambda-64-1.svg" alt="Kinesis Logo" width="100"/>
AWS Lambda is a serverless compute service that automatically processes data from Kinesis streams.  
Lambda polls and reads streaming data, enabling near real-time event-driven processing without server management.

---

### 4. Amazon Kinesis Data Firehose  
<img src="https://cdn.worldvectorlogo.com/logos/amazon-kinesis-1.svg" alt="Kinesis Logo" width="100"/>
Amazon Kinesis Data Firehose automates capture, transformation, and loading (ETL) of streaming data into destinations like Amazon S3.  
Think of it as similar to Azure Data Factory but specialized for streaming data.

---

### 5. Data Storage Layers in Amazon S3  

| Layer           | Description                                                                                  | Icon                                         |
|-----------------|----------------------------------------------------------------------------------------------|----------------------------------------------|
| **Archive**     | S3 bucket for archiving incoming files, useful for troubleshooting and audits.              | <img src="https://cdn.worldvectorlogo.com/logos/amazon-s3-simple-storage-service.svg" alt="Kinesis Logo" width="100"/>       |
| **Stage**       | First landing zone in S3 where data from Kinesis is stored for next-level processing.        | <img src="https://cdn.worldvectorlogo.com/logos/amazon-s3-simple-storage-service.svg" alt="Kinesis Logo" width="100"/>|
| **Processing**  | The stage where transformation and business logic happen (AWS Glue, PySpark, EMR, Databricks) |<img src="https://cdn.worldvectorlogo.com/logos/apache-spark-5.svg" alt="Kinesis Logo" width="100"/> |
| **Raw**         | Processed data archive bucket allowing audits and error tracing.                            | <img src="https://cdn.worldvectorlogo.com/logos/amazon-s3-simple-storage-service.svg" alt="Kinesis Logo" width="100"/>|
| **Curated**     | Final processed data stored in Delta format, ready for analytics and querying.               | <img src="https://cdn.worldvectorlogo.com/logos/amazon-s3-simple-storage-service.svg" alt="Kinesis Logo" width="100"/> |

---

### 6. AWS SNS (Simple Notification Service)  
<img src="https://cdn.worldvectorlogo.com/logos/aws-sns.svg" alt="Kinesis Logo" width="100"/> 
Amazon SNS sends notifications to subscribed endpoints upon new data availability, ensuring real-time alerts.

---

### 7. Amazon Athena  
<img src="https://th.bing.com/th/id/OIP.J0Fifz1PbF2ra7Gxw84JEgHaFO?w=241&h=180&c=7&r=0&o=7&dpr=1.3&pid=1.7&rm=3" alt="Kinesis Logo" width="100"/> 
Amazon Athena allows **serverless SQL querying** over data stored in S3, enabling easy and scalable data analysis directly on the curated datasets.

---

### 8. Apache Airflow  
<img src="https://tse4.mm.bing.net/th/id/OIP.tiQmc-cX-G7FZf0JgAt9aAHaLb?rs=1&pid=ImgDetMain&o=7&rm=3" alt="Kinesis Logo" width="100"/> 
Apache Airflow orchestrates and automates the entire pipeline with **DAG-based scheduling**, managing dependencies and monitoring workflow execution.

---

## 🎯 Highlights  
- Real-time ingestion & processing with Kinesis & Lambda.  
- Automated ETL workflows via Apache Airflow.  
- Scalable, secure multi-layered storage with Amazon S3.  
- Instant notifications with SNS.  
- Serverless, interactive queries via Athena.

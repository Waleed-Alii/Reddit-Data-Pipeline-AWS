# Reddit Data Engineering Pipeline
## Orchestrated with Airflow, Celery, Postgres, S3, AWS Glue, Athena, and Redshift

This project implements a robust ETL pipeline to extract, transform, and load Reddit data into an AWS Redshift data warehouse. It utilizes a modern data engineering stack including Apache Airflow for orchestration, S3 for data lake storage, and AWS Glue/Athena for transformations.

## Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [System Setup](#system-setup)
- [Usage](#usage)

## Overview
The pipeline automates the following workflow:
1. **Extraction**: Pulling data from Reddit using the PRAW (Python Reddit API Wrapper).
2. **Staging**: Storing raw JSON/CSV data into an Amazon S3 bucket.
3. **Transformation**: Processing and cleaning data using AWS Glue and Amazon Athena.
4. **Loading**: Moving the structured data into Amazon Redshift for analytics.

## Architecture
![Architecture Diagram](assets/RedditDataEngineering.png)

## Tech Stack
*   **Orchestration:** Apache Airflow, Celery
*   **Containerization:** Docker, Docker Compose
*   **Data Lake:** Amazon S3
*   **Data Warehouse:** Amazon Redshift
*   **Compute/Transformation:** AWS Glue, Amazon Athena
*   **Database:** PostgreSQL (Metastore)
*   **Language:** Python 3.9+

## Prerequisites
*   AWS Account with S3, Glue, Athena, and Redshift access.
*   Reddit Developer Account (API credentials).
*   Docker & Docker Compose installed locally.

## System Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Waleed-Alii/Reddit-Data-Pipeline-AWS.git
   ```

2. **Configure Credentials**:
   Edit `config/config.conf` with your specific API and AWS keys:
   ```ini
   [api_keys]
   reddit_secret_key = [YOUR SECRET]
   reddit_client_id = [YOUR ID]

   [aws]
   aws_access_key_id = [YOUR ACCESS KEY]
   aws_secret_access_key = [YOUR SECRET KEY]
   aws_region = [YOUR REGION]
   aws_bucket_name = [YOUR S3 BUCKET]
   ```

3. **Start the environment**:
   ```bash
   docker-compose up -d
   ```

4. **Access Airflow**:
   Navigate to `http://localhost:8080` (Default Credentials: `admin` / `admin`)

## Usage
1. Once in the Airflow UI, locate the `etl_reddit_pipeline` DAG.
2. Unpause the DAG (toggle the switch to "On").
3. Trigger the DAG manually or wait for the daily schedule.
4. Monitor the task progress in the Graph/Tree view.

## Author
**Waleed Ali**
*   GitHub: [Waleed-Alii](https://github.com/Waleed-Alii)

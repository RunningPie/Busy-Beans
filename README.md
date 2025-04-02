# BusyBeans: Café Activity Tracker

BusyBeans is a web-based application that tracks and visualizes the least and most busy cafés in a specific area. It leverages modern data engineering tools and techniques to scrape, process, and visualize café activity data.

## Architecture Overview

Below is the architecture diagram for BusyBeans:

```plaintext
+-------------------+
|   Google Maps     |
|   (Dynamic Page)  |
+-------------------+
         ↓
+-------------------+
|   Web Scraping    |
|   (Playwright)    |
+-------------------+
         ↓
+-------------------+
|   Message Queue   |
|   (Apache Kafka)  |
+-------------------+
         ↓
+-------------------+
|   Data Lake       |
|   (HDFS/Hadoop)   |
+-------------------+
         ↓
+-------------------+
|   Data Processing |
|   (Apache Spark)  |
+-------------------+
         ↓
+-------------------+
|   Structured Data |
|   (Apache Iceberg)|
+-------------------+
         ↓
+-------------------+
| Workflow Orchest- |
| ration (Airflow)  |
+-------------------+
         ↓
+-------------------+
|   Structured Data |
|   (Apache Iceberg)|
+-------------------+
         ↓
+-------------------+
| Workflow Orchest- |
| ration (Airflow)  |
+-------------------+
         ↓
+-------------------+
|   Dashboard       |
|   (Streamlit)     |
+-------------------+
         ↓
+-------------------+
|   Deployment      |
|   (Docker)        |
+-------------------+
         ↓
+-------------------+
| Monitoring & Logs |
|   (Apache Beam)  |
+-------------------+
```

| **COMPONENT**           | **TOOL**             | **PURPOSE**                                                                 |
|-------------------------|----------------------|-----------------------------------------------------------------------------|
| Data Source             | Google Maps          | Scrape café data (names, ratings, place busyness, etc.).                    |
| Web Scraping            | Playwright           | Extract dynamic content from Google Maps pages.                             |
| Message Queue           | Apache Kafka         | Stream scraped data in real-time for processing.                            |
| Data Lake               | HDFS (Apache Hadoop) | Store raw scraped data in a distributed file system.                        |
| Data Processing         | Apache Spark         | Process raw data to calculate metrics like "busyness score."                |
| Structured Data Storage | Apache Iceberg       | Store processed data in an optimized, ACID-compliant table format.          |
| Workflow Orchestration  | Apache Airflow       | Automate and schedule workflows (e.g., scraping → processing → dashboard).  |
| Dashboard               | Streamlit            | Visualize insights like least/most busy cafés in an interactive web app.    |
| Deployment              | Docker               | Containerize the application for consistent deployment across environments. |
| Monitoring & Logging    | Apache Beam         | Collect and monitor logs from the pipeline components.                      |

## Getting Started
### Prerequisites

* Python 3.x
* Docker
* Apache Kafka
* Hadoop (for HDFS)
* Apache Spark
* Apache Airflow
* Apache Iceberg
* Apache Flume
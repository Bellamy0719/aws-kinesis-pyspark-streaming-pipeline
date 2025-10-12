# aws-kinesis-pyspark-streaming-pipeline
### Real-time data streaming pipeline on AWS using Kinesis and PySpark Structured Streaming.
### >  This project extends the batch data lakehouse pipeline:
> [aws-pyspark-data-lakehouse-pipeline](https://github.com/Bellamy0719/aws-pyspark-data-lakehouse-pipeline)

### 🧠 Project Overview

This project simulates real-time stock price streaming using AWS and Databricks.
It reads 2024 historical data from S3, sends it to Kinesis as a live data feed,
processes it in Databricks Structured Streaming, computes rolling metrics,
and stores aggregated results back into S3 for downstream analytics.

### ✅ Key Highlights

Real-time streaming with AWS Kinesis
Processing with Databricks Structured Streaming (PySpark)
Partitioned Parquet output to S3
Query layer via AWS Glue + Athena
Dashboard visualization in QuickSight

**Real-Time Stock Data Streaming Architecture**
```

┌───────────────────────────┐
│ S3 Historical Data (2024) │
└────────────┬──────────────┘
             │
             ▼
      Python Producer  
     (send to Kinesis)
             │
             ▼
     Amazon Kinesis Stream  
     (real-time ingestion)
             │
             ▼
   Databricks Notebook (Structured Streaming)
   ├─ Parse JSON from Kinesis  
   ├─ Compute avg_1min / latest_close            --- real time visualization
   ├─ Display real-time metrics  
   └─ Write results to S3 (Parquet)
             │
             ▼
      S3 Streaming Output  
   (checkpoint + parquet results)
```
```
aws-databricks-realtime-stock-streaming/
│
├── notebooks/
│   ├── producer_kinesis.py
│   ├── consumer_databricks_streaming.py
│   └── display_avg_1min.png
│
├── assets/
│   ├── architecture_diagram.png
│   ├── quicksight_dashboard.png
│   ├── athena_query.png
│   ├── s3_structure.png
│   ├── kinesis_console.png
│
└── README.md
```


# aws-kinesis-pyspark-streaming-pipeline
### Real-time data streaming pipeline on AWS using Kinesis and PySpark Structured Streaming.
### >  This project extends the batch data lakehouse pipeline:
> [aws-pyspark-data-lakehouse-pipeline](https://github.com/Bellamy0719/aws-pyspark-data-lakehouse-pipeline)



```
**Real-Time Stock Data Streaming Architecture**

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

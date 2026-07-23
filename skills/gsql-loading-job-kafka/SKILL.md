---
name: gsql-loading-job-kafka
description: >
  Configure real-time loading jobs to consume and upsert streaming data from Apache Kafka. Use when establishing live event streaming pipelines.
license: MIT
---
# Streaming Data from Apache Kafka

## When to use this
Use when loading streaming business events, transaction logs, or IoT data into TigerGraph in near-real-time.

## Prerequisites
Running Kafka broker, target topic, and TigerGraph Kafka connector setup. Links:
- [Kafka Loading Reference](https://docs.tigergraph.com)

## Steps
1. Create a loading job configuring the Kafka data mapping:
   ```gsql
   USE GRAPH Social_Network
   CREATE LOADING JOB load_kafka FOR GRAPH Social_Network {
       DEFINE FILENAME f = "kafka_config.json";
       LOAD f TO VERTEX User VALUES ($0, $1, $2) USING SEPARATOR=",";
   }
   ```
2. Create the configuration file `kafka_config.json` containing brokers and topic details:
   ```json
   {
       "broker.list": "localhost:9092",
       "topic": "user_events"
   }
   ```
3. Run the streaming job, which will remain active and process events as they arrive:
   ```gsql
   RUN LOADING JOB load_kafka USING f="kafka_config.json"
   ```

## Common mistakes
- Failing to allocate partition offsets correctly, which can cause duplicate loads or missing messages.
- Running real-time streaming loads on a compute-constrained node, which causes thread starvation and query latency spikes.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)

# Real-Time E-Commerce Analytics Pipeline

An end-to-end data engineering project that explores Change Data Capture (CDC) to process e-commerce sales data and support near-real-time analytics.

## Overview

Traditional analytics pipelines often rely on periodic data exports, which can introduce delays and increase the workload on operational databases.

This project demonstrates a CDC-based architecture designed to capture database changes, stream events through Kafka, process data with Spark Structured Streaming, and make analytical data available in ClickHouse.

## Architecture

```text
PostgreSQL
    |
    v
Debezium CDC Connector
    |
    v
Apache Kafka
    |
    v
Spark Structured Streaming
    |
    v
ClickHouse
    |
    v
Analytics Dashboard
```

## Technology Stack

- **PostgreSQL** — Relational source database
- **Debezium** — Change Data Capture
- **Apache Kafka** — Event streaming and message transport
- **Apache Spark Structured Streaming** — Stream processing
- **ClickHouse** — Analytical database
- **Docker Compose** — Containerized environment
- **Python** — Event generation and data processing scripts
- **Apache Superset** — Dashboarding, if configured in the project environment

## Project Structure

```text
.
├── create_tables.sql
├── docker-compose.yml
├── eventgenerator.py
├── kafka_to_clickhouse.py
├── postgres-source.json
├── spark_job.py
└── .gitignore
```

## Main Components

- `create_tables.sql`: SQL script for database table creation.
- `docker-compose.yml`: Docker Compose configuration for the project services.
- `eventgenerator.py`: Python script for generating events or sample data.
- `postgres-source.json`: Configuration for the PostgreSQL source connector.
- `kafka_to_clickhouse.py`: Python component for transferring Kafka events to ClickHouse.
- `spark_job.py`: Spark processing job.

## Getting Started

### Prerequisites

- Docker Desktop
- Python
- Git

Additional dependencies and service requirements depend on the configurations used in `docker-compose.yml` and the Python scripts.

### 1. Clone the repository

```bash
git clone https://github.com/hodamounaouir/real-time-ecommerce-analytics.git
cd real-time-ecommerce-analytics
```

### 2. Start the services

Review `docker-compose.yml` and configure any required environment variables before starting the containers.

```bash
docker compose up -d
```

### 3. Configure the CDC connector

Review `postgres-source.json` and adapt the connector settings to your local environment. Register the connector using the Debezium Connect REST API if that service is configured in your Docker environment.

### 4. Run the processing components

Review the Python scripts and their dependencies before executing the event generator, Kafka consumer, or Spark job. Run each component according to the configuration of your environment.

## Expected Outcome

The intended workflow is to capture changes from PostgreSQL, transport events through Kafka, process streaming data, and store analytical results in ClickHouse for querying and visualization.

## Future Improvements

- Add automated data quality checks.
- Add monitoring and error-handling mechanisms.
- Document deployment and recovery procedures.
- Include dashboard screenshots and measured latency results.

## Author

**Hoda MOUNAOUIR**  
Engineering Student in Information Systems Engineering & Big Data

- GitHub: [@hodamounaouir](https://github.com/hodamounaouir)

---

*This repository is a learning project focused on CDC, event streaming, and real-time data engineering.*

# Data-Science-Tools

### Big data processing

When datasets don’t fit in memory:

* **Apache Spark**\
  Still the standard for distributed batch processing and ETL pipelines.
* **Apache Flink**\
  Increasingly used for real-time analytics and event-driven systems.
* SQL engines on distributed systems:
  * Trino (formerly Presto)
  * DuckDB (fast-growing for local analytics and embedded SQL)

### Cloud data warehouses & lakehouse systems

Modern data science is heavily cloud-native:

* **Snowflake**\
  Leading cloud data warehouse with strong separation of storage/compute.
* **Google Cloud BigQuery**\
  Serverless analytics, widely used for large-scale SQL workloads.
* **Databricks**\
  Popularizes the “lakehouse” model (combining data lakes + warehouses) and deeply integrates Spark + ML tooling.
* **Amazon Web Services (Redshift, Athena, SageMaker)**\
  Broadest service ecosystem for data + ML pipelines.

### MLOps (productionizing models)

This is one of the fastest-evolving areas:

* Model tracking: MLflow, Weights & Biases
* Pipeline orchestration: Airflow, Prefect, Dagster
* Deployment: Kubernetes, Docker
* Feature stores: Feast, Tecton
* Monitoring: Evidently AI, Arize

The goal is reproducibility, versioning, and continuous model updates.

### Visualization & BI

* matplotlib / seaborn (classical Python visualization)
* Plotly, Dash (interactive dashboards)
* Tableau / Power BI (enterprise BI layer)
* Superset / Metabase (open-source alternatives)


# Patient Churn Prediction Workspace

## Overview
This workspace implements a full pipeline for predicting patient churn using Databricks and MLflow. It covers data ingestion, transformation, model training, inference, and risk segmentation.

## Data Pipeline
* **Bronze Stage**: Raw patient data is ingested and stored in the `bronze_patients` table.
* **Silver Stage**: Data is cleaned and transformed, resulting in the `silver_patients` table.
* **Gold Stage**: Model inference is performed on silver data, generating churn scores and risk segments, saved in the `gold_patients` table.

## Model Training & Inference
* Model is trained and logged using MLflow (see `ml_train` notebook).
* Inference is performed in the `gold` notebook:
  * Loads the latest model from MLflow Registry.
  * Applies the model to silver patient data.
  * Calculates churn probability and assigns risk segments.
  * Saves results to the gold table.
  * Computes churn score statistics and saves to `churn_data` table.

## Usage Instructions
1. Run the notebooks in order: `set_up` →  `ml_train` →  `synthetic_data` → `bronze` → `silver` → `gold`.
2. Ensure Unity Catalog volumes and tables exist as referenced in the code.
3. Review outputs in the gold and churn_data tables for patient risk segmentation and churn analytics.

## Key Tables
* `patient_churn_prediction.patient_data.bronze_patients`
* `patient_churn_prediction.patient_data.silver_patients`
* `patient_churn_prediction.patient_data.gold_patients`
* `patient_churn_prediction.patient_data.churn_data`

* [Watch Presentation Video](https://youtu.be/KXz8nO0grDg?si=a8-l1mNOpWITYkfC)
* [Linkedin Profile](www.linkedin.com/in/sridharccc)

## Dependencies
* Databricks Runtime (Serverless cluster)
* MLflow
* PySpark

---
For more details, review the individual notebooks for code logic and customization options.

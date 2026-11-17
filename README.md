# ERP Event Logs: KPI Extraction and Forecasting

## Introduction

ERP systems record a single business process across many tables, making it difficult to consistently extract and compare key performance indicators (KPIs). The selected paper, “ERP Event Logs: A Canonical Form for KPI Time-Series Extraction and Characterization,” addresses this problem by converting ERP transactions into a common event-log structure built around a case, activity, and timestamp.

Using this canonical representation, organizations can reuse the same operations to study order-to-cash and procure-to-pay processes. The project follows this approach to calculate KPI volumes, durations, and rates—such as order volume, delivery time, payment time, supplier lead time, and cancellation rate—and explores simple forecasting and model comparison using weekly KPI data.

The paper’s original SAP customer transactions are proprietary, so the accompanying notebook uses a small illustrative event-log dataset to demonstrate the extraction and forecasting workflow.

[Medium article](https://medium.com/@manalivijay.mankad/from-orders-to-forecasts-understanding-erp-event-logs-and-kpis-2f9e6f81a9c3?sharedUserId=manalivijay.mankad)

[Paper](https://arxiv.org/pdf/2610.09903)

[Google Colab notebook](https://colab.research.google.com/drive/1N1w2FmDunQLWxrwUBE-AvjTq7Pg7HW5x?usp=sharing)

[YouTube video](https://youtu.be/Wa5t_VPQUUk)

# 🏗 Architecture Diagram Explanation

This document explains the design choices shown in our deployment architecture diagram.

## 📊 Overview

- *GitHub / Local Files:* Acts as simulated Azure Blob Storage for storing datasets.
- *Google Colab + Pandas:* Simulates Azure Data Factory, handling ingestion, cleaning, filtering, and output.
- *Pandas DataFrame:* Simulates Azure SQL DB for temporary structured data processing.
- *Power BI:* Used for visualization.

## 🔄 Data Flow

1. Raw CSV is uploaded to GitHub / Colab.
2. Data is processed in Colab (cleaned, filtered, converted).
3. Output stored as cleaned CSV and HTML table.
4. Power BI reads these for dashboards.

## 🗂 Diagram File Location

The actual diagram is saved as:

- /diagrams/deployment_architecture.png

and also maintained in /diagrams/deployment_architecture.drawio for future edits.

# 🛡️ Safety Sync Flow

## 🧭 Overview
**Safety Sync Flow** is a Microsoft Power Automate flow designed to run at scheduled intervals to fetch safety-related reports from an external safety management system via HTTP calls. The data is parsed, transformed, and then stored in the Quattrofy SQL Database, where it powers real-time reporting via Power BI dashboards embedded into the Quattrofy platform.

## 💡 Objective
To automate the synchronization of key safety data between the third-party safety software and the internal Quattrofy system. The flow reduces manual reporting tasks, improves data visibility for leadership, and eliminates the need for expensive customizations on the external platform.

## ✨ Features
- Scheduled execution (every few hours)
- HTTP GET calls to a safety system’s Open API
- Data extraction, transformation, and normalization
- Writes directly to Quattrofy’s Azure SQL Database
- Logs each sync operation for traceability
- Integration with Power BI for safety analytics dashboards

## 🧪 Data Extracted
- **Incident Reports**
- **FLHA (Field Level Hazard Assessments)**
- **Safety Inspections**
- **Project Safety Metrics**
- **Date, Location, Risk Level, Resolutions**

## ⚙️ Tech Stack

| Category        | Technologies |
|----------------|--------------|
| **Automation** | ![Power Automate](https://img.shields.io/badge/Power%20Automate-0089D6?logo=Microsoft%20Power%20Automate&logoColor=white&style=for-the-badge) |
| **API Access** | ![REST API](https://img.shields.io/badge/REST%20API-0052CC?logo=postman&logoColor=white&style=for-the-badge) |
| **Database**   | ![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?logo=microsoft-sql-server&logoColor=white&style=for-the-badge), ![Azure SQL](https://img.shields.io/badge/Azure%20SQL-0078D4?logo=microsoft-azure&logoColor=white&style=for-the-badge) |
| **Visualization** | ![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black&style=for-the-badge) |
| **Hosting**    | ![Microsoft Azure](https://img.shields.io/badge/Azure-0078D4?logo=microsoft-azure&logoColor=white&style=for-the-badge) |

## 🔄 Flow Logic
1. **Trigger:** Recurring (every X hours)
2. **HTTP Request:** Pull latest records from `/incidents`, `/flha`, and `/inspections` endpoints
3. **Data Processing:** Clean and reshape JSON data into relational format
4. **Insert:** Push the cleaned data into staging tables in Azure SQL
5. **Log & Notify:** Log the run results and send success/failure summary via email

## 📊 Power BI Integration
All transferred safety data is visualized in Quattrofy’s **Safety Dashboard**. 

This module was developed collaboratively:
- You handled **data extraction**, **API transformation**, and **database ingestion**
- The **Project Controls Manager** developed the Power BI dashboards, formulas, visualizations, and UX design

The resulting dashboard allows executives to:
- View safety performance by project and department
- Track incident trends and resolution time
- Monitor FLHA and inspection frequency
- Identify compliance gaps in near real-time

## 🤖 Impact
- ⏳ Reduced manual entry time by 95%
- 📈 Provided high-level insight into safety metrics
- 💬 Enabled directors to make proactive HSE decisions
- 💸 Eliminated external dev costs by building in-house sync flow

## 🔐 Notes
- Built-in failure alerts and retry policies
- Can be extended to pull additional safety datasets
- Optimized for low-maintenance and security (OAuth tokens for API)

## 🔗 Related Projects
- `Quattrofy` – Main Web Application
- `Safety Dashboards (Power BI)` – Interactive visualizations
- `Sync Projects Flow` – Similar syncing architecture

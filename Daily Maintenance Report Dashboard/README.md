# Daily Maintenance Report Dashboard

## Overview

This Power BI solution automates the daily maintenance reporting routine of a tire manufacturing plant, replacing a fully manual process of compiling operational data for the plant's daily management meeting.

The dashboard consolidates, in a single interactive report, all maintenance events that generated production losses in the previous day, the status of the monthly preventive maintenance plan, drum changeover performance against the 60-minute target, and a monthly summary of the tracked indicators — segmented by shift, tire type, area and production division.

---

## Business Problem

Before this solution, the daily maintenance report was produced manually.

Every morning, the maintenance team had to open the maintenance management system, review **work order by work order**, and manually transcribe machine, shift, downtime, problem, root cause and corrective action into a document to be presented at the plant's daily meeting.

This process was:

- Time-consuming and repetitive
- Prone to transcription errors
- Impossible to scale across two production divisions
- Unable to provide consolidated monthly trends
- Dependent on individual effort rather than a standardized process

There was also no consolidated view of preventive maintenance progress or drum changeover performance, which made it difficult to anticipate deviations before the end of the month.

---

## Solution

The dashboard was built on a simple and reliable data flow:

```text
Maintenance Management System (CMMS)
              ↓
        Excel (structured input)
              ↓
        Power Query (ETL)
              ↓
       Data Model + DAX Measures
              ↓
        Power BI Dashboard
```

Once the Excel source is updated, refreshing the report automatically delivers every table and indicator required for the daily meeting — with no manual compilation.

---

## Dashboard Structure

The report is organized into eight pages covering two production divisions.

### 1. Daily Maintenance Report — Division A

Detailed event-level table containing area, category, shift, downtime (minutes), machine, intervention type, problem, root cause and corrective action, with total downtime for the selected day.

**Filters:** date, machine, intervention type.

### 2. Daily Summary — Division A

Visual breakdown of the same day:

- Total downtime (minutes)
- Downtime by machine and intervention type
- Downtime distribution by intervention type
- Machine and shift reference table

### 3. Monthly Report — Division A

Consolidated monthly performance:

- Total monthly downtime
- Downtime by area
- Downtime by shift
- Top machines by downtime
- Pareto analysis of downtime by intervention type (absolute and percentage)

### 4. Daily Maintenance Report — Division B

Event-level table including **production losses**, with category, shift, tire type, SKU, tires lost, downtime, machine, intervention type, problem, root cause and corrective action.

**KPIs:** daily tire losses and daily downtime.

### 5. Daily Summary — Division B

- Tires lost and downtime for the day
- Downtime and losses by machine and intervention type
- Losses by production area
- Tire type filter

### 6. Monthly Report — Division B

- Downtime and losses by area
- Total losses by shift
- Losses by tire type
- Top 5 machines by downtime
- Top 5 machines by tire losses, broken down by tire type

### 7. Drum Changeover Performance

Dedicated page monitoring changeover time on tire building machines against a **60-minute target** (80 minutes for a specific machine group).

- Average changeover time by machine group over time
- Light and heavy tire changeover summaries
- Total changeovers by machine group
- Total simultaneous changeovers

### 8. Preventive Maintenance Control

Side-by-side control of both divisions:

- Scheduled preventive maintenances
- Completed preventive maintenances
- Completed vs. remaining by area
- Detailed list of date, area and machine

---

## Key Performance Indicators

| KPI | Description |
|---|---|
| Daily Downtime (min) | Total maintenance downtime for the selected day |
| Monthly Downtime (min) | Accumulated downtime in the month |
| Downtime by Area | Downtime split by production area |
| Downtime by Shift | Downtime split by work shift |
| Downtime by Intervention Type | Corrective, jam and adjustment breakdown with Pareto view |
| Daily Tire Losses | Tires lost due to maintenance events |
| Losses by Tire Type | Losses segmented by product type |
| Top Machines by Downtime | Ranking of most critical machines |
| Top Machines by Losses | Ranking by production impact |
| Average Changeover Time | Drum changeover time by machine group vs. 60 min target |
| Total Changeovers | Volume of changeovers by machine group |
| Simultaneous Changeovers | Concurrent changeover events |
| Scheduled PMs | Preventive maintenances planned in the period |
| Completed PMs | Preventive maintenances executed |
| Remaining PMs | Preventive maintenances still pending by area |

---

## Main Filters

- Date and date range
- Month
- Machine
- Intervention type
- Production area
- Shift
- Tire type

---

## Data Model

The model was designed to serve two divisions with different analytical needs while sharing the same date and machine dimensions.

**Main components**

- Maintenance events fact table (downtime, losses, problem, cause, action)
- Preventive maintenance schedule and execution
- Drum changeover records
- Machine dimension (machine, area, category, group)
- Calendar dimension
- Intervention type dimension
- Tire type / SKU dimension

**Technical implementation**

- Power Query for cleaning, standardization and consolidation of Excel sources
- Star schema modeling with shared dimensions across divisions
- DAX measures for daily, monthly and target-based calculations
- Time intelligence for monthly accumulation and daily comparison
- Ranking measures for Top N analysis

---

## Technologies Used

- Power BI
- DAX
- Power Query (M)
- Microsoft Excel
- Data Modeling
- Data Visualization

---

## Business Impact

The solution replaced a manual, work-order-by-work-order reporting routine with an automated analytical report.

**Key benefits**

- Elimination of manual daily report compilation
- Standardized reporting format across two production divisions
- Immediate visibility of downtime, root causes and corrective actions for the daily plant meeting
- Traceability of production losses by machine, tire type, shift and area
- Continuous monitoring of drum changeover performance against target
- Real-time follow-up of preventive maintenance plan execution
- Faster, evidence-based discussion of the previous day's performance
- Historical monthly view enabling trend and recurrence analysis

The report is used daily by maintenance supervisors and managers as the official input for the plant's daily operational meeting.

---

## Screenshots

### 1. Daily Maintenance Report — Division A

Event-level maintenance report with problem, root cause, corrective action and downtime per work order.

<img width="1600" height="900" alt="Relatório diário - DIV A" src="https://github.com/user-attachments/assets/4d73e4fd-b855-4a8f-9ac1-2534eae4fe0c" />

### 2. Daily Summary — Division A

Visual breakdown of downtime by machine and intervention type.

<img width="1600" height="900" alt="Resumo diário - DIV A" src="https://github.com/user-attachments/assets/2f31a677-6170-46a5-b2d5-2621f16c312e" />

### 3. Monthly Report — Division A

Monthly consolidation by area, shift, machine and intervention type.

<img width="1600" height="900" alt="Relatório Mensal - DIV A" src="https://github.com/user-attachments/assets/c373d653-a530-44ed-8cee-b26e0b9d2547" />

### 4. Daily Maintenance Report — Division B

Daily report including tire losses by SKU and tire type.

<img width="1600" height="900" alt="Relatório diário - DIV B" src="https://github.com/user-attachments/assets/3b3d89b2-2062-4b27-8331-eecf6c6e193e" />

### 5. Daily Summary — Division B

Downtime and production losses by machine and intervention type.

<img width="1600" height="900" alt="Resumo diário - DIV B" src="https://github.com/user-attachments/assets/a09874c0-54c2-4743-94b8-31d5231a83a7" />

### 6. Monthly Report — Division B

Monthly losses and downtime with Top 5 machine rankings.

<img width="1600" height="900" alt="Relatório Mensal - DIV B" src="https://github.com/user-attachments/assets/888807aa-b067-4d1d-b30c-635477e25fb7" />

Changeover time monitoring by machine group against the 60-minute target.

<img width="1600" height="900" alt="Relatório de Trocas" src="https://github.com/user-attachments/assets/43d8404d-b0f7-442f-925b-a59f27e6dc43" />

### 8. Preventive Maintenance Control

Scheduled vs. completed preventive maintenance for both divisions.

<img width="1600" height="900" alt="Relatório de Preventivas" src="https://github.com/user-attachments/assets/3fb4c35d-5ec6-4956-ad19-ea6f3aa01806" />

---

## Technical Skills Demonstrated

- Power BI report development for operational routines
- Multi-source data consolidation with Power Query
- Star schema data modeling
- DAX measure development (aggregations, rankings, time intelligence, target analysis)
- KPI design for maintenance and reliability management
- Manufacturing downtime and production loss analysis
- Preventive maintenance compliance tracking
- Report automation and process standardization

---

## Author

**Thiago Keidi Kimura Medici**

Maintenance Engineering • Data Analytics • Power BI • DAX • Excel • Industrial Performance Analysis

---

### Disclaimer

All data presented in this project was anonymized and adapted for portfolio purposes. Company identification, equipment codes and operational details have been modified or removed to preserve confidentiality.

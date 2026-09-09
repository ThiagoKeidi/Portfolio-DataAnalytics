# Maintenance Cost Control Dashboard

## Overview

This Power BI solution monitors structural maintenance spending across the plant's machine groups, converting a purchase requisition spreadsheet into an interactive cost control tool.

The dashboard consolidates every purchase requisition classified as **structural maintenance** — spare parts, materials, external services and contracts — and breaks the spending down by machine group, by individual machine and down to the requisition line item, allowing area supervisors to track expenditure against the cost target throughout the period.

---

## Business Problem

Maintenance purchase requisitions were recorded in a spreadsheet containing every purchase made by the department, regardless of its nature.

To understand how much was actually being spent on **structural maintenance** of the machines, supervisors had to manually inspect the purchase justification of each requisition, classify it, and then aggregate the values by machine or production line.

This made it difficult to:

- Separate structural maintenance spending from other purchases
- Know how much each machine group was consuming
- Identify which specific machines were driving the cost
- Trace a spending figure back to the individual requisitions behind it
- Follow expenditure against the cost target during the period
- Support purchase decisions with consolidated evidence

There was no consolidated cost view — only a transactional list of requisitions.

---

## Solution

The dashboard is fed by a single structured requisition spreadsheet and applies the business classification logic inside the ETL layer.

```text
Purchase Requisition Spreadsheet
              ↓
   Power Query (ETL + classification)
   • filters purchases justified as STRUCTURAL
   • maps justification / place of use to machine group
              ↓
        Data Model + DAX Measures
              ↓
        Power BI Dashboard
```

### Source fields

| Field | Description |
|---|---|
| Requisition Date | Date the purchase requisition was issued |
| Requisition ID | Unique requisition number |
| Value (BRL) | Order amount |
| Item Description | Description of the purchased item |
| Quantity | Quantity ordered |
| Unit of Measure | Unit associated with the quantity |
| Stock Code / Commodity | Inventory code, when applicable, to support future purchases |
| Supplier | Vendor responsible for the order |
| Justification / Place of Use | Purchase justification — the field that drives structural classification and machine group allocation |

The **Justification / Place of Use** field is the core of the model: it determines whether the requisition enters the dashboard and to which machine group it is allocated.

---

## Dashboard Structure

### 1. Cost Overview by Machine Group

Executive view of total structural maintenance spending.

- **Total Spend** KPI for the selected period
- Spending by machine group, ranked from highest to lowest
- Data slicer for period selection

This page answers the first question of any cost review: *where is the money going?*

### 2. Cost Breakdown by Machine

Drill-down of the same total into individual machines.

- Spending per machine, ranked in descending order
- Immediate identification of the assets concentrating the cost
- Long-tail visibility of low-cost machines

This page supports Pareto reasoning — a small number of machines typically concentrates the majority of the structural spending.

### 3. Requisition Detail

Transactional level, with navigation buttons for each machine group.

- Date range slicer (start and end date)
- Group navigation buttons: general structural and each production line
- Detailed table with requisition date, requisition ID, value, item description, quantity with unit of measure, and stock / commodity code
- Running total of the filtered selection

This page guarantees full traceability: every figure shown in the charts can be traced back to the exact requisitions that generated it.

---

## Key Performance Indicators

| KPI | Description |
|---|---|
| Total Structural Spend | Total amount spent on structural maintenance in the period |
| Spend by Machine Group | Cost distribution across production lines and general structural |
| Spend by Machine | Cost concentration at individual asset level |
| Spend by Requisition | Transactional detail of each purchase order |
| Spend vs. Target | Expenditure monitored against the defined cost target |
| Cost Ranking | Machines and groups ordered by consumption |

---

## Main Filters

- Date range (start and end date)
- Period selection
- Machine group navigation (general structural and production lines)

---

## Data Model

**Main components**

- Purchase requisition fact table (date, requisition ID, value, quantity, item)
- Machine and machine group dimension
- Item / commodity dimension (stock code, description, unit of measure)
- Supplier dimension
- Calendar dimension

**Technical implementation**

- Power Query for cleaning, standardization and consolidation of the requisition spreadsheet
- Business rule applied in the ETL to isolate structural maintenance purchases
- Text-based classification mapping the justification field to the corresponding machine group
- Star schema modeling
- DAX measures for totals, group aggregation, ranking and target comparison
- Bookmark and button navigation for group-level drill-down

**MODEL SCREENSHOT**

<img width="1393" height="1129" alt="WhatsApp Image 2026-09-09 at 13 49 17" src="https://github.com/user-attachments/assets/3f596543-1a20-4a7d-b1bf-c11b9866eb0d" />

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

The dashboard turned a transactional purchase spreadsheet into a maintenance cost management tool.

**Key benefits**

- Automatic separation of structural maintenance spending from general purchases
- Clear visibility of cost distribution across machine groups and individual machines
- Identification of the assets concentrating maintenance expenditure
- Continuous follow-up of spending against the cost target
- Full traceability from consolidated figures down to individual requisitions
- Faster and better-supported purchase decisions
- Standardized item and stock code reference to support future purchases
- Elimination of manual classification and aggregation of requisitions

The report is used by area supervisors to monitor structural maintenance expenditure of their machines.

---

## Screenshots

### 1. Cost Overview by Machine Group

Total structural maintenance spending with breakdown by machine group.

<img width="1600" height="900" alt="WhatsApp Image 2026-09-09 at 13 44 14" src="https://github.com/user-attachments/assets/36a29b37-aeca-4bc3-b171-6838673d8460" />

### 2. Cost Breakdown by Machine

Spending distribution across individual machines, ranked by cost.

<img width="1600" height="900" alt="WhatsApp Image 2026-09-09 at 13 44 13 (1)" src="https://github.com/user-attachments/assets/6cd85fda-6f76-490b-a053-a6cf201b30fe" />

### 3. Requisition Detail

Transactional view with date range filtering, group navigation and item-level detail.

<img width="1600" height="900" alt="WhatsApp Image 2026-09-09 at 13 44 13" src="https://github.com/user-attachments/assets/87605306-f55d-488a-82f8-50f4a6f97da8" />

---

## Technical Skills Demonstrated

- Power BI dashboard development for cost management
- ETL development with Power Query
- Business rule implementation in the data transformation layer
- Text-based classification of free-form justification fields
- Star schema data modeling
- DAX measure development (aggregation, ranking, target comparison)
- Maintenance cost analysis
- Drill-down and navigation design with bookmarks and buttons
- Spend traceability and auditability

---

## Author

**Thiago Keidi Kimura Medici**

Maintenance Engineering • Data Analytics • Power BI • DAX • Excel • Industrial Performance Analysis

---

### Disclaimer

All data presented in this project was anonymized and adapted for portfolio purposes. Company identification, supplier names, item codes, monetary values and equipment identification have been modified or removed to preserve confidentiality.

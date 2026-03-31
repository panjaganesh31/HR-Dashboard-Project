# 📊 HR Dashboard — Microsoft Fabric Project

> An end-to-end HR Analytics solution built on **Microsoft Fabric** — from raw data ingestion to interactive Power BI reporting.

<img width="959" height="476" alt="Dashboard Image" src="https://github.com/user-attachments/assets/33b72829-23e9-49fe-8ee3-f49e451ad71d" />


---

## 🏗️ Architecture Overview

```
Excel / CSV Source
        │
        ▼
┌─────────────────────┐
│  HR_Dashboard_      │  ← Dataflow Gen2 (Power Query / M Language)
│  Dataflow           │     • Data cleaning & transformation
│                     │     • Age Bracket custom column
│                     │     • 39 columns, 311 rows
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  HR_Dashboard_      │  ← Microsoft Fabric Lakehouse (Delta Tables)
│  Lakehouse          │     • HRDataset table (311 rows × 39 columns)
│                     │     • SQL Analytics Endpoint enabled
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  HR_Dashboard_      │  ← Semantic Model (DAX Measures & Relationships)
│  Semantic_Model     │     • KPIs: HeadCount, Attrition, Avg Salary
│                     │     • Upstream: Lakehouse + Dataflow
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  HR Dashboard       │  ← Power BI Report (Interactive Visuals)
│  Report             │     • Filters: Dept, Position, Gender, State
│                     │     • 6 chart types + 5 KPI cards
└─────────────────────┘
         ▲
         │
┌─────────────────────┐
│  HR_Dashboard_      │  ← Data Pipeline (Orchestration)
│  Refresh_Pipeline   │     • Hr_Dataflow → HR_Semantic_Model_Refresh
└─────────────────────┘
```

---

## 📁 Project Components

| # | Component | Type | Description |
|---|-----------|------|-------------|
| 1 | **HR Dashboard** | Power BI Report | Interactive HR analytics with filters & 6 visuals |
| 2 | **HR_Dashboard_Dataflow** | Dataflow Gen2 | ETL — loads, cleans & transforms HR data |
| 3 | **HR_Dashboard_Lakehouse** | Lakehouse | Central Delta Lake store — HRDataset table |
| 4 | **HR_Dashboard_Lakehouse** | SQL Analytics Endpoint | Direct SQL query access on Lakehouse |
| 5 | **HR_Dashboard_Refresh_Pipeline** | Data Pipeline | Orchestrates Dataflow → Semantic Model refresh |
| 6 | **HR_Dashboard_Semantic_Model** | Semantic Model | Business logic, DAX measures & KPIs |

---

## 📊 Dashboard KPIs & Visuals

### 🔢 KPI Cards
| Metric | Value |
|--------|-------|
| **HeadCount** | 311 |
| **Attrition** | 104 |
| **Attrition %** | 0.33 |
| **Average Salary** | $69.02K |
| **Average Age** | 47.41 |

### 📈 Charts & Visuals
| Visual | Description |
|--------|-------------|
| **HeadCount by Department** | Bar chart — Production leads with 209 employees |
| **HeadCount by Age Bracket** | Donut chart — 36–45 age group is largest (47.91%) |
| **HeadCount by Marital Status & Gender** | Grouped bar — Male vs Female breakdown |
| **HeadCount by Recruitment Source** | Bar chart — Indeed (100) is top source |
| **Attrition by Year** | Line chart — 2008–2014 trend |
| **Cumulative HeadCount by Year** | Dual line — growth trend to 310 |

### 🎛️ Filters Available
- Department | Position | Employment Status | Gender | State

---

## 🗄️ Dataset Details

**Table:** `HRDataset` in `HR_Dashboard_Lakehouse`

| Property | Value |
|----------|-------|
| Rows | 311 |
| Columns | 39 |
| Key columns | Employee_Name, EmpID, GenderID, DeptID, MaritalStatusID, EmpStatusID, PerfScoreID |

---

## 🔄 Pipeline Flow

```
HR_Dashboard_Refresh_Pipeline
        │
        ├──► [1] Hr_Dataflow          (Dataflow Gen2 refresh)
        │
        └──► [2] HR_Semantic_Model_Refresh   (triggered after Dataflow ✅)
```

> Pipeline ensures data stays fresh — Dataflow runs first, then Semantic Model auto-refreshes.

---

## 🔗 Semantic Model Lineage

| Item | Type | Relation |
|------|------|----------|
| HR Dashboard | Report | ⬇️ Downstream |
| HR_Dashboard_Dataflow | Dataflow Gen2 | ⬆️ Upstream |
| HR_Dashboard_Lakehouse | Lakehouse | ⬆️ Upstream |

---

## 🛠️ Tech Stack

| Technology | Usage |
|------------|-------|
| **Microsoft Fabric** | Workspace, Lakehouse, Dataflow Gen2, Pipeline |
| **Power BI** | Report & Semantic Model |
| **Delta Lake** | Storage format in Lakehouse |
| **DAX** | Measures — HeadCount, Attrition %, Avg Salary, Avg Age |
| **Power Query / M** | Dataflow transformations — Age Bracket, custom columns |
| **SQL Analytics Endpoint** | Direct SQL on Lakehouse tables |

---

## 📸 Screenshots

### HR Dashboard Report
<img width="959" height="476" alt="Dashboard Image" src="https://github.com/user-attachments/assets/3fb774df-ca50-45fc-83e4-0f187fbd0141" />


### Lakehouse — HRDataset Table
<img width="959" height="472" alt="Lakehouse " src="https://github.com/user-attachments/assets/5fb4714a-a338-4f62-a754-57291e454d0d" />


### Dataflow — Power Query Transformations
<img width="959" height="472" alt="Dataflow Image" src="https://github.com/user-attachments/assets/d10e1f71-a6f9-4d4b-979d-5acd0d8168ce" />


### Refresh Pipeline
<img width="959" height="476" alt="HR Dashboard Pipeline" src="https://github.com/user-attachments/assets/fbbc8f01-956a-4fdb-b658-c9206da1cc77" />


### Semantic Model — Lineage View
<img width="953" height="473" alt="Dashboard Semantic Model" src="https://github.com/user-attachments/assets/5821035a-4a53-4533-9037-e6c6d5915b7b" />



## 🙏 Acknowledgements

- Built on **Microsoft Fabric** (Preview / Trial)
- HR Dataset — sample employee data for analytics demonstration
- Inspired by real-world HR analytics use cases


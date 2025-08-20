# 🌾 End-to-End Data Pipeline: AWS S3 → Snowflake → Power BI  

## 🚨 Problem I Solved  
Working with agricultural data, I noticed organizations struggle with **scattered datasets across different systems**.  
They need a way to:  
- Consolidate raw data into a single location.  
- Transform it into **business-ready formats**.  
- Build **interactive dashboards** to track rainfall, temperature, humidity, and crop yields.  

This project solves that problem by building an **end-to-end cloud data pipeline** using **AWS S3, Snowflake, and Power BI**.  

---

## 🔎 What I Built  
I created a complete cloud data pipeline that:  
- Takes raw CSV data from **AWS S3**  
- Processes it in **Snowflake**  
- Visualizes it through **Power BI dashboards**  

**Architecture Flow:**  
`AWS S3 (Raw Data Storage) → Snowflake (Data Processing) → Power BI (Analytics & Dashboards)`  

---

## ⚙️ Step-by-Step Implementation  

### 1. Setting Up AWS S3 Storage  
- Created an S3 bucket called `powerbix.project`.  
- Uploaded dataset `data_season.csv`.  

![S3 Upload](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/snapshot-1.png)

---

### 2. Configuring Security with IAM  
- Created IAM role `powerBI.role` with full S3 access permissions.  
- Retrieved ARN for Snowflake integration.  

![IAM Role](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/snapshot-2.png)

---

### 3. Connecting Snowflake to AWS  
- Created **integration object** `PBI_integration` in Snowflake.  
- Updated AWS IAM **Trust Policy** with Snowflake ARN & External ID.  

![Snowflake Integration](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/snapshot-3.png)

---

### 4. Loading Data into Snowflake  
- Created:  
  - Database: `powerBI`  
  - Schema: `PBI_Data`  
  - Table: `PBI_DataSet`  
- Created **Stage** object referencing S3.  
- Used `COPY INTO` to load **3,158 rows**.  

![Snowflake Load 1](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/snapshot-4.png)  
![Snowflake Load 2](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/snapshot-5.png)

---

### 5. Data Transformation and Cleaning  
Performed profiling:  
- Checked nulls, min/max, distinct values.  

Transformations applied:  
- Boosted rainfall values by **+10%**  
- Reduced area values by **-10%**  
- Added `year_group` column (y1, y2, y3)  
- Added `rainfall_groups` column (low, medium, high)  

![Transformations](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/snapshot-6.png)

---

### 6. Bringing Data into Power BI  
- Connected Power BI → **Snowflake Connector**.  
- Used account URL & warehouse (`compute_wh`).  
- Imported transformed dataset & validated in Power Query Editor.  

![Power BI Import](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/snapshot-7.png)

---

### 7. Building the Dashboard  
Created a **4-page Power BI report**:  
1. **Rainfall Analysis** → Avg rainfall by year, season, crop, location  
2. **Temperature Analysis** → Temp trends across dimensions  
3. **Humidity Analysis** → Humidity patterns  
4. **Yield Analysis** → Crop yield performance metrics  

![Rainfall](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/Rainfall%20analysis.png)  
![Temperature](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/Temperature%20analysis.png)  
![Humidity](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/Humidity%20analysis.png)  
![Yield](https://github.com/nileshdeb/Cloud-Data-Pipeline-Analytics/blob/main/Yield%20analysis.png)

---

## 📚 What I Learned  
- Setting up **AWS-Snowflake IAM integration** and trust policies.  
- Importance of **data profiling** before transformations.  
- Designing **clean dashboards** with Power BI.  
- How cloud tools work together in a modern **data pipeline**.  

---

## ✅ Results  
- Automated processing of agricultural data.  
- **Scalable & secure pipeline** from raw data → insights.  
- Interactive dashboards for **real-time decision-making**.  
- Helps stakeholders analyze **weather patterns, yields, and trends** easily.  

---

## 🛠️ Tech Stack  
- **AWS S3** → Raw data storage  
- **AWS IAM** → Secure role-based access  
- **Snowflake** → Data warehouse & transformations  
- **Power BI** → Analytics dashboards  


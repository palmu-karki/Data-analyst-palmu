  # Projects

## **Phase 1**

### **Project Title:** Descriptive Analysis of Ortho Photo Imagery Dataset in the City of Vancouver

### **Objective:**  
To provide a descriptive breakdown of the Ortho Photo Imagery dataset, assess its structure, quality, and key characteristics, and provide insights into how it can be used for geospatial analysis and mapping. This includes examining the dataset's properties such as image resolution, coordinates, and timestamps, and identifying any patterns or anomalies that could affect data quality and usage.

### **Dataset:**
- **Dataset Type:** Ortho Photo Imagery (Geospatial Data)
- **Data Size:** The dataset consists of images captured from aerial surveys, typically in the form of GeoTIFF files, with coordinates (latitude, longitude), image resolution, and timestamp information for each image.
- **Scope:** Covers a specific geographic region (e.g., a city or county), typically for the year 2022 or the most recent available year.
- **Data Points:** Each image contains geospatial metadata, including:
  - **Resolution:** Pixel density and clarity.
  - **Coordinates:** GPS coordinates (latitude, longitude) of the image's coverage area.
  - **Timestamp:** The time the image was captured.
  - **Other Metadata:** Camera settings, flight altitude, and other geospatial reference information.

### **Methodology:**

#### **1. Data Collection and Ingestion:**
- The raw ortho photo imagery dataset is ingested into an AWS S3 bucket from a remote server using AWS services.![image](https://github.com/user-attachments/assets/17795c8c-1739-4960-8e38-edb995c48752)
![image](https://github.com/user-attachments/assets/a834bc73-d51f-41b1-80ec-65481ac9796a)

- The dataset is stored in raw format and is accessible for processing, cleaning, and analysis.

#### **2. Data Profiling:**
- The dataset is assessed for completeness and consistency. This involves reviewing key attributes such as image resolution and coordinates.
- An initial review identifies potential issues such as missing geospatial metadata, resolution inconsistencies, or timestamps that are out of range.
  

**Steps:**
- Use **AWS Glue Data Brew** to perform data profiling on the images, extracting key insights about the resolution, geospatial information, and timestamp consistency.![image](https://github.com/user-attachments/assets/3a0c7b9b-1918-4cbc-916d-c2c4dcbba996)

- Run statistical analysis on the metadata to identify anomalies (such as missing values or outliers).

#### **3. Data Cleaning:**
![image](https://github.com/user-attachments/assets/b1b82c61-7498-44a2-b81f-1c8c58f28a77)

**Steps:**
- Handle missing values using interpolation techniques for geospatial data (coordinates).
- Remove duplicate entries or images captured redundantly.
- Ensure consistent formats for timestamps and coordinates.

#### **4. Data Cataloging and Structuring:**

- After cleaning, the dataset is cataloged using **AWS Glue Data Catalog**, which makes it easier to query and access the data in future analyses.
- Geospatial data such as coordinates and image resolution are indexed for faster retrieval.

**Steps:**
- Register the cleaned dataset in the AWS Glue catalog.
- Ensure proper structuring of the dataset for use in geospatial analysis.

#### **5. Data Summarization and Initial Insights:**
![image](https://github.com/user-attachments/assets/2b173f9e-6ca5-49e4-8104-a415e47fc86a)
![image](https://github.com/user-attachments/assets/6f00ccf0-e6f1-4a79-9069-1cc9825af93c)

- The data is summarized using descriptive statistics and visualizations.
- Insights are drawn from patterns related to image resolution, geographic distribution, and temporal trends.

**Steps:**
- Run SQL queries in **Amazon Athena** to extract and summarize key statistics (e.g., image resolution averages, coordinate range, timestamp trends).
- Visualize trends such as variations in image resolution across the geographic region or changes in captured imagery over time.

#### **6. Visualization and Mapping:**
- Data visualizations are created to illustrate the relationship between geospatial features (coordinates) and other dataset attributes, such as image resolution or timestamp.
- Interactive maps or graphs are generated to visualize areas covered by high-resolution images and those with potential quality issues.

### **Tools and Techniques:**
- **AWS Services:** S3, Glue Data Brew, Glue Crawler, ETL pipelines.
- **Data Processing:** ETL pipeline with AWS Glue, Data Cleaning with Data Brew.
- **Data Storage:** Cloud-based AWS databases, S3 buckets.

### **Deliverables:**
1. **Cleaned Dataset:** Stored in S3 in CSV/Parquet formats.
2. **Descriptive Analysis Report:** Summarizing key findings and insights.
3. **Visualizations and Dashboards:** Graphs and maps illustrating data trends, resolution patterns, and geographical coverage.
4. **Recommendations Document:** Suggestions for improving image collection and data processing workflows.

---

## **Data Quality Control: Ensuring Clean and Reliable Data for the City of Vancouver**

### **Project Title:** Implementation of Data Quality Control Measures for Ortho Photo Imagery – City of Vancouver

### **Objective:**
To implement data quality control techniques using rule-based validation pipelines and continuous monitoring mechanisms, ensuring that the dataset adheres to high standards of data integrity, reliability, and consistency.

### **Background:**
As the City of Vancouver transitions into cloud-based analytics, maintaining data quality has become crucial. The dataset often contains:
- Duplicates
- Missing or incomplete fields
- Inconsistent formats

This initiative implements automated validation, real-time quality metrics, and visual dashboards to govern and enhance dataset integrity.

### **Scope:**
This Data Quality Control (DQC) framework includes:
- **Data Profiling** – Initial quality analysis
- **Data Cleansing** – Removing or correcting flawed entries
- **Validation** – Automated rule-based checks
- **Monitoring & Reporting** – Dashboards for real-time oversight
- **Governance & Awareness** – Implementation via ETL and role-based visibility

### **Methodology:**

#### **1. Current State Assessment:**
- Analyzed the raw dataset structure, volume, and frequency of ingestion.
- Evaluated duplication issues in categorical fields and null entries.

#### **2. Data Profiling:**
- Used **AWS Glue DataBrew** for initial profiling.
- **Key insights:**
  - ~1% missing values in `GeoLocalArea`
  - Fields were predominantly **String** and **Double**

#### **3. Data Cleansing Process:**
Handled during **DataBrew** transformation:
- Removed nulls from `GeoLocalArea`
- Converted all columns to **CamelCase**
- Trimmed whitespaces
- Standardized categorical formats

#### **4. Validation Rules and ETL Pipeline:**
Built a **visual ETL pipeline in AWS Glue** for validation:![image](https://github.com/user-attachments/assets/bb7ca7a4-06b9-47a4-bfbe-d5e5aa869cfb)


1. **Extract:** Data pulled from transformed S3 bucket.
2. **Evaluate:** Applied uniqueness rule.
3. **Result Column:** Added `evaluation_result` status (Passed or Default).
4. **Conditional Routing:** Filtered based on evaluation result.
5. **Split Output:** Segregated data into **passed** and **default** branches.
6. **Drop Columns:** Removed unnecessary metadata.
7. **Auto-Balancing:** Optimized for partitioning.
8. **Load:** Exported to **S3** with separate folders for each result.

#### **5. Monitoring and Reporting:**
![image](https://github.com/user-attachments/assets/d4c64bd4-8658-4669-a81c-d66daea67c12)
![image](https://github.com/user-attachments/assets/5f541e2f-1b49-4ddb-bf3c-e6f6152f7ac6)


 Monitored dataset using **AWS CloudWatch** to visualize:
- Data quality performance
- AWS resource usage
- Pipeline health and compliance

### **Tools & Technologies:**
| Tool | Purpose |
|------|---------|
| **AWS Glue ETL** | Visual ETL for evaluating data rules |
| **Amazon S3** | Raw and cleaned data storage |
| **AWS CloudWatch** | Monitoring job runs and performance |
| **DataBrew** | Profiling & transformation |
| **CSV/Parquet Outputs** | Final validated datasets |

### **Deliverables:**
✅ **ETL pipeline** for rule-based data quality validation  
📊 **Quality Check reports** (Passed/Default segregation)  
🖼️ **Dashboard** with real-time monitoring of data metrics  
📝 **Full documentation** of data quality rules, thresholds, and output structure  

### **Conclusion:**
This **Data Quality Control** implementation provides the City of Vancouver with a strong foundation for maintaining trusted, validated datasets. By combining **rule-based validation, segregated output pipelines, and monitoring dashboards**, the platform ensures **scalable and transparent data governance** across departments.


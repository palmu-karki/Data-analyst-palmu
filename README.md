# Data-analyst-palmu
**Phase 1**

**Project Title:** Descriptive Analysis of Ortho Photo Imagery Dataset


## **Objective:**  
The primary objective of this analysis is to provide a descriptive breakdown of the Ortho Photo Imagery dataset, assess its structure, quality, and key characteristics, and provide insights into how it can be used for geospatial analysis and mapping. This includes examining the dataset's properties such as image resolution, coordinates, and timestamps, and identifying any patterns or anomalies that could affect data quality and usage.


### **Dataset:**
- **Dataset Type:** Ortho Photo Imagery (Geospatial Data)
- **Data Size:** The dataset consists of images captured from aerial surveys, typically in the form of GeoTIFF files, with coordinates (latitude, longitude), image resolution, and timestamp information for each image.
- **Scope:** The dataset covers a specific geographic region (for example, a city or county), typically for the year 2022 or the most recent available year.
- **Data Points:** Each image contains geospatial metadata, including:
  - **Resolution:** Pixel density and clarity.
  - **Coordinates:** GPS coordinates (latitude, longitude) of the image's coverage area.
  - **Timestamp:** The time the image was captured.
  - **Other Metadata:** Camera settings, flight altitude, and other geospatial reference information.

### **Methodology:**

#### **1. Data Collection and Ingestion:**
- The raw ortho photo imagery dataset is ingested into an AWS S3 bucket from a remote server using AWS services.![image](https://github.com/user-attachments/assets/810c6cb4-8f5e-43c5-8c82-bad83b4922d7)
![image](https://github.com/user-attachments/assets/9802a3e7-db00-4ff7-bfad-f0e42ea39158)

- The dataset is stored in raw format and is accessible for processing, cleaning, and analysis.

#### **2. Data Profiling:**
- The dataset is assessed for completeness and consistency. This involves reviewing key attributes such as image resolution, coordinates, and timestamps. ![image](https://github.com/user-attachments/assets/9974be5e-01a3-44b3-a0b2-c83af8ee996c)

- An initial review identifies potential issues such as missing geospatial metadata, resolution inconsistencies, or timestamps that are out of range.


**Steps:**
- Use **AWS Glue Data Brew** to perform data profiling on the images, extracting key insights about the resolution, geospatial information, and timestamp consistency.
- Run statistical analysis on the metadata to identify anomalies (such as missing values or outliers).

#### **3. Data Cleaning:**
![image](https://github.com/user-attachments/assets/02df108b-0eb9-4e41-a2d1-1a9b96a0d35a)![image](https://github.com/user-attachments/assets/98f7e6ab-eee4-4a83-bdc2-a4df45ed6ead)

**Steps:**
- Handle missing values using interpolation techniques for geospatial data (coordinates).
- Remove duplicate entries or images captured redundantly.
- Ensure consistent formats for timestamps and coordinates.

#### **4. Data Cataloging and Structuring:**
- After cleaning, the dataset is cataloged using **AWS Glue Data Catalog**, which makes it easier to query and access the data in future analyses.![image](https://github.com/user-attachments/assets/46dfeee8-e295-44de-9d33-42cf12797475)

- Geospatial data such as coordinates and image resolution are indexed for faster retrieval.

**Steps:**
- Register the cleaned dataset in the AWS Glue catalog.
- Ensure proper structuring of the dataset for use in geospatial analysis.

#### **5. Data Summarization and Initial Insights:**
- The data is summarized using descriptive statistics and visualizations. ![image](https://github.com/user-attachments/assets/df0727f3-d01b-410d-83f1-6f94e0af988b)

- Insights are drawn from patterns related to image resolution, geographic distribution, and temporal trends.

**Steps:**
- Run SQL queries in **Amazon Athena** to extract and summarize key statistics (e.g., image resolution averages, coordinate range, timestamp trends).
- Visualize trends such as variations in image resolution across the geographic region or changes in captured imagery over time.

#### **6. Visualization and Mapping:**
- Data visualizations are created to illustrate the relationship between geospatial features (coordinates) and other dataset attributes, such as image resolution or timestamp.
- Interactive maps or graphs are generated to visualize areas covered by high-resolution images and those with potential quality issues.


### **Tools and Techniques:**
AWS Services: S3, Glue Data Brew, Glue Crawler, ETL pipelines.
Data Processing: ETL pipeline with AWS Glue, Data Cleaning with Data Brew.
Data Storage: Cloud-based AWS databases, S3 buckets.

### **Deliverables:**
1. **Cleaned Dataset:** The dataset after cleaning and cataloging will be stored in S3 in CSV/Parquet formats.
2. **Descriptive Analysis Report:** Detailed report summarizing key findings and insights.
3. **Visualizations and Dashboards:** Graphs and maps illustrating data trends, resolution patterns, and geographical coverage.
4. **Recommendations Document:** A report detailing suggestions for improving image collection and data processing workflows.

This descriptive analysis provides a thorough overview of the Ortho Photo Imagery dataset, emphasizing data quality, patterns, and areas for improvement. By leveraging AWS tools and geospatial software, the dataset can be effectively processed and analyzed to provide actionable insights for urban planning, environmental monitoring, or other spatial-based initiatives.





# Failed_Banks-fgic.gov-Report
A Python and Power BI analysis exploring trends in U.S. bank failures. The project cleans and visualises closing‑date data to identify yearly patterns, peak failure periods, and institutional activity. It demonstrates core data skills and translates raw data into clear, actionable business insights.”  

# 📊 Failed Banks Trend Analysis (Python + Power BI)  
This project analyses the trend of failed banks in the United States using Python and Power BI.

It is designed as a beginner‑friendly data analysis project demonstrating:
- Data cleaning
- Date handling
- Trend analysis
- Visualisation
- Dashboard design
- Business insights

# 🔍 Key Questions Answered
- How has the number of failed banks changed over time?
- Which years recorded the highest number of failures?
- Which states experienced the most failures?
- Which institutions acquired the most failed banks?

# 🧪 Tools Used
- Python (Pandas, Matplotlib)
- Power BI
- GitHub

# 🧠 Insights
- Bank failures vary significantly year to year.
- Certain years show clear spikes, indicating periods of financial stress.
- Some states consistently appear among the highest failure counts.
- Acquiring institutions show patterns of consolidation.

# Python Analysis

import pandas as pd  
df = pd.read_csv('Failed Bank (fgic.gov)download-data.csv', encoding='latin1')  

df.head(10)
<img width="963" height="444" alt="image" src="https://github.com/user-attachments/assets/f4e6150b-ae9d-41cd-8c7c-6b401684de2f" />  

# How many banks failed each year?  
df.columns  
<img width="1595" height="118" alt="image" src="https://github.com/user-attachments/assets/45f85e2f-8d1e-4e50-a7e4-a823119f8bed" />  

# Cleaning the Columns  

df.columns = df.columns.str.strip()        # remove spaces  
df.columns = df.columns.str.replace(' ', '_')  # replace spaces with _  

df['Closing_Date'].head(10)
<img width="1605" height="289" alt="image" src="https://github.com/user-attachments/assets/04690500-00e3-4dc4-801e-edbcd0056527" />  

df['Closing_Date'] = pd.to_datetime(df['Closing_Date'], format='%Y-%m-%d')  
df['Year'] = df['Closing_Date'].dt.year  
df['Year'].value_counts().sort_index()  
<img width="1608" height="574" alt="image" src="https://github.com/user-attachments/assets/5a8f4120-90d2-45da-ac29-3f05210fbca3" />  

# Which year had the highest number of failures?   
df['Year'].value_counts().idxmax()  
df['Year'].value_counts().idxmin()  
<img width="1574" height="173" alt="image" src="https://github.com/user-attachments/assets/a505d81e-7d1e-42a2-a0ba-3102e50d730f" />  

# PLOT THE TREND  
##Plot the number of failed banks per year  

import matplotlib.pyplot as plt

failures_per_year = df['Year'].value_counts().sort_index()

plt.figure(figsize=(10,5))
plt.plot(failures_per_year.index, failures_per_year.values, marker='o')
plt.title('Number of Failed Banks Per Year')
plt.xlabel('Year')
plt.ylabel('Number of Failed Banks')
plt.grid(True)
plt.show()

<img width="1561" height="776" alt="image" src="https://github.com/user-attachments/assets/3dc6c1e0-8a00-42da-8850-504f697cba1b" />  

##Top 5 top Failed banks per year
df['Year'].value_counts().head()

<img width="1625" height="301" alt="image" src="https://github.com/user-attachments/assets/7c8f5f5e-ad4f-49e9-b36a-c7562711ada5" />  

# 📌 Insights from the Trend of Failed Banks

## 1. Year‑to‑Year Variation
The number of failed banks changes significantly across years. Some years show only a few failures, while others show noticeable spikes.

## 2. Peak Failure Years
By checking:
df['Year'].value_counts().head()  
You can identify the top failure years. These represent periods of financial stress or regulatory changes.  

## 3. Recent Trends
The most recent years in your dataset show whether failures are increasing, decreasing, or stabilising.

## 4. Business Interpretation
A spike in failures may indicate economic downturns, liquidity issues, or regulatory tightening.  
A decline suggests improved financial stability or stronger oversight.  
Consistent low numbers indicate a stable banking environment.  




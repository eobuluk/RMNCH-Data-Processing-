# Data Processing of RMNCH DATA
Refining Reproductive, Maternal, Newborn, and Child Health (RMNCH) Data: Cleaning and Preprocessing for Accurate Maternal and Child Health Insights
## Objective:
This project aimed to enhance the accuracy, usability, and reliability of Reproductive, Maternal, Newborn, and Child Health (RMNCH) data. The primary goal was to transform raw, inconsistent data into a clean, structured format, enabling accurate analysis and actionable insights for program evaluation and decision-making.
## Key Tasks and Processes:
• Handled missing values: Identified columns with missing data to ensure completeness during analysis, and filled missing values with zeros to maintain dataset consistency and avoid errors.
• Removed duplicate records: Detected and removed duplicate rows to ensure unique and accurate data entries
• Standardized column names: Stripped leading/trailing whitespace and converted column names to lowercase for consistency and
ease of use
## Outcome:
These data cleaning steps ensured that the dataset was well structured, with no missing values or duplicates, and that the column names were standardized. This provided a clean dataset for the next stages of analysis.
## Tools and technologies used:
• Python: Utilized Pandas for data manipulation and cleaning
• Jupyter Notebook: Documented and visualized the entire workflow for reproducibility
## Python Code and Results:
Below was the Python Code used to for data cleaning and the output of the results:

 "## Loading the Dataset\n",
    "The dataset used in this project contained 429 rows and 36 columns, representing data related to reproductive, maternal, newborn, and child health (RMNCH) collected from 18 districts in Southwest Uganda over a period of 8 years (2015 - 2022). It included information on various indicators such as antenatal care visits, deliveries, maternal deaths, and child health outcomes across different periods and regions.\n",
    "\n",
    "- The first step in the data analysis process was to load and inspect the dataset into Python to inspect and clean it. The data set was stored in an Excel file (.xlxs). \n",
    "- I used the pandas library to manipulate and analyze the data in order to understand its structure, identify any potential data quality issues such as missing or inconsistent values, and prepare it for further analysis. \n",
    "\n",
    "The following Python code below was used to load the dataset into a pandas DataFrame for further data exploration:"
```python
# Import pandas to handle the data
import pandas as pd
# Load the dataset
file_path = '/Users/mac/Desktop/RMNCH_Data.xlsx'
df = pd.read_excel(file_path)
# Display the first few rows of the dataset
df.head()

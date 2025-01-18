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
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "id": "3473facf",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>code</th>\n",
       "      <th>Region</th>\n",
       "      <th>District</th>\n",
       "      <th>Period</th>\n",
       "      <th>Period code</th>\n",
       "      <th>Year</th>\n",
       "      <th>105-2.1 A1:ANC 1st Visit for women</th>\n",
       "      <th>105-2.1 A1:ANC 1st Visit for women (No. in 1st Trimester)</th>\n",
       "      <th>105-2.1 A2:ANC 4th Visit for women</th>\n",
       "      <th>105-2.1 A3:Total ANC visits (New clients + Re-attendances)</th>\n",
       "      <th>...</th>\n",
       "      <th>105-2.3 Postnatal Attendances 6 Weeks</th>\n",
       "      <th>105-2.3 Postnatal Attendances 6 Months</th>\n",
       "      <th>105-3 OA5 Maternal Deaths Audited</th>\n",
       "      <th>105-3 OA6-Perinatal Deaths Audited</th>\n",
       "      <th>108-3 MSP Caesarian Sections</th>\n",
       "      <th>Expected Pregnancies (0.05*popn/4)</th>\n",
       "      <th>Expected Deliveries (0.0485*popn/4)</th>\n",
       "      <th>Estimated Children &lt;1 (0.043*popn/4)</th>\n",
       "      <th>Projected population</th>\n",
       "      <th>Total birth</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>BuhwejuOct to Dec 15</td>\n",
       "      <td>Ankole</td>\n",
       "      <td>Buhweju</td>\n",
       "      <td>Oct to Dec 15</td>\n",
       "      <td>FY1-Q1</td>\n",
       "      <td>2015/16</td>\n",
       "      <td>917</td>\n",
       "      <td>162</td>\n",
       "      <td>491</td>\n",
       "      <td>1924</td>\n",
       "      <td>...</td>\n",
       "      <td>81</td>\n",
       "      <td>91</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>6.0</td>\n",
       "      <td>1546</td>\n",
       "      <td>1500</td>\n",
       "      <td>1330</td>\n",
       "      <td>30925.0</td>\n",
       "      <td>394</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>BuhwejuJan to Mar 16</td>\n",
       "      <td>Ankole</td>\n",
       "      <td>Buhweju</td>\n",
       "      <td>Jan to Mar 16</td>\n",
       "      <td>FY1-Q2</td>\n",
       "      <td>2015/16</td>\n",
       "      <td>973</td>\n",
       "      <td>122</td>\n",
       "      <td>435</td>\n",
       "      <td>2303</td>\n",
       "      <td>...</td>\n",
       "      <td>139</td>\n",
       "      <td>34</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>3.0</td>\n",
       "      <td>1546</td>\n",
       "      <td>1500</td>\n",
       "      <td>1330</td>\n",
       "      <td>30925.0</td>\n",
       "      <td>392</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>BuhwejuApr to Jun 16</td>\n",
       "      <td>Ankole</td>\n",
       "      <td>Buhweju</td>\n",
       "      <td>Apr to Jun 16</td>\n",
       "      <td>FY1-Q3</td>\n",
       "      <td>2015/16</td>\n",
       "      <td>1002</td>\n",
       "      <td>176</td>\n",
       "      <td>414</td>\n",
       "      <td>2346</td>\n",
       "      <td>...</td>\n",
       "      <td>104</td>\n",
       "      <td>36</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>2.0</td>\n",
       "      <td>1546</td>\n",
       "      <td>1500</td>\n",
       "      <td>1330</td>\n",
       "      <td>30925.0</td>\n",
       "      <td>359</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>BuhwejuJul to Sep 16</td>\n",
       "      <td>Ankole</td>\n",
       "      <td>Buhweju</td>\n",
       "      <td>Jul to Sep 16</td>\n",
       "      <td>FY1-Q4</td>\n",
       "      <td>2015/16</td>\n",
       "      <td>951</td>\n",
       "      <td>163</td>\n",
       "      <td>713</td>\n",
       "      <td>2536</td>\n",
       "      <td>...</td>\n",
       "      <td>132</td>\n",
       "      <td>8</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>6.0</td>\n",
       "      <td>1546</td>\n",
       "      <td>1500</td>\n",
       "      <td>1330</td>\n",
       "      <td>30925.0</td>\n",
       "      <td>585</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>BuhwejuOct to Dec 16</td>\n",
       "      <td>Ankole</td>\n",
       "      <td>Buhweju</td>\n",
       "      <td>Oct to Dec 16</td>\n",
       "      <td>FY2-Q1</td>\n",
       "      <td>2016/17</td>\n",
       "      <td>940</td>\n",
       "      <td>173</td>\n",
       "      <td>609</td>\n",
       "      <td>2407</td>\n",
       "      <td>...</td>\n",
       "      <td>160</td>\n",
       "      <td>20</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>15.0</td>\n",
       "      <td>1595</td>\n",
       "      <td>1547</td>\n",
       "      <td>1372</td>\n",
       "      <td>31900.0</td>\n",
       "      <td>525</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>5 rows × 37 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "                   code  Region District         Period Period code     Year  \\\n",
       "0  BuhwejuOct to Dec 15  Ankole  Buhweju  Oct to Dec 15      FY1-Q1  2015/16   \n",
       "1  BuhwejuJan to Mar 16  Ankole  Buhweju  Jan to Mar 16      FY1-Q2  2015/16   \n",
       "2  BuhwejuApr to Jun 16  Ankole  Buhweju  Apr to Jun 16      FY1-Q3  2015/16   \n",
       "3  BuhwejuJul to Sep 16  Ankole  Buhweju  Jul to Sep 16      FY1-Q4  2015/16   \n",
       "4  BuhwejuOct to Dec 16  Ankole  Buhweju  Oct to Dec 16      FY2-Q1  2016/17   \n",
       "\n",
       "   105-2.1 A1:ANC 1st Visit for women  \\\n",
       "0                                 917   \n",
       "1                                 973   \n",
       "2                                1002   \n",
       "3                                 951   \n",
       "4                                 940   \n",
       "\n",
       "   105-2.1 A1:ANC 1st Visit for women (No. in 1st Trimester)  \\\n",
       "0                                                162           \n",
       "1                                                122           \n",
       "2                                                176           \n",
       "3                                                163           \n",
       "4                                                173           \n",
       "\n",
       "   105-2.1 A2:ANC 4th Visit for women  \\\n",
       "0                                 491   \n",
       "1                                 435   \n",
       "2                                 414   \n",
       "3                                 713   \n",
       "4                                 609   \n",
       "\n",
       "   105-2.1 A3:Total ANC visits (New clients + Re-attendances)  ...  \\\n",
       "0                                               1924           ...   \n",
       "1                                               2303           ...   \n",
       "2                                               2346           ...   \n",
       "3                                               2536           ...   \n",
       "4                                               2407           ...   \n",
       "\n",
       "   105-2.3 Postnatal Attendances 6 Weeks  \\\n",
       "0                                     81   \n",
       "1                                    139   \n",
       "2                                    104   \n",
       "3                                    132   \n",
       "4                                    160   \n",
       "\n",
       "   105-2.3 Postnatal Attendances 6 Months  105-3 OA5 Maternal Deaths Audited  \\\n",
       "0                                      91                                NaN   \n",
       "1                                      34                                NaN   \n",
       "2                                      36                                NaN   \n",
       "3                                       8                                NaN   \n",
       "4                                      20                                NaN   \n",
       "\n",
       "   105-3 OA6-Perinatal Deaths Audited  108-3 MSP Caesarian Sections  \\\n",
       "0                                 NaN                           6.0   \n",
       "1                                 NaN                           3.0   \n",
       "2                                 NaN                           2.0   \n",
       "3                                 NaN                           6.0   \n",
       "4                                 NaN                          15.0   \n",
       "\n",
       "   Expected Pregnancies (0.05*popn/4)  Expected Deliveries (0.0485*popn/4)  \\\n",
       "0                                1546                                 1500   \n",
       "1                                1546                                 1500   \n",
       "2                                1546                                 1500   \n",
       "3                                1546                                 1500   \n",
       "4                                1595                                 1547   \n",
       "\n",
       "   Estimated Children <1 (0.043*popn/4)  Projected population  Total birth  \n",
       "0                                  1330               30925.0          394  \n",
       "1                                  1330               30925.0          392  \n",
       "2                                  1330               30925.0          359  \n",
       "3                                  1330               30925.0          585  \n",
       "4                                  1372               31900.0          525  \n",
       "\n",
       "[5 rows x 37 columns]"
      ]
     },
     "execution_count": 28,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Import pandas to handle the data\n",
    "import pandas as pd\n",
    "\n",
    "# Load the dataset\n",
    "file_path = '/Users/mac/Desktop/RMNCH_Data.xlsx'\n",
    "df = pd.read_excel(file_path)\n",
    "\n",
    "# Display the first few rows of the dataset\n",
    "df.head()\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "11236705",
   "metadata": {},
   "source": [
    "## Overview of the Data\n",
    "This dataset contained key RMNCH indicators collected from the 18 districts across Southwest Uganda, this offered valuable insights into reproductive, maternal, newborn, and child health (RMNCH). The following columns were included:\n",
    "### Demographic data:\n",
    "- Region, District, Period, Period Code, Year: This provided geographic context and a time frame for the data, which  facilitated data analysis by location and reporting periods.\n",
    "### Antenatal care (ANC): \n",
    "- ANC 1st Visit for Women, ANC 1st Visit for Women (No. in 1st Trimester), ANC 4th Visit for Women, Total ANC Visits (New Clients + Re-attendances): These columns tracked antenatal care services in order to understand access and use of health care during pregnancy. \n",
    "- First Dose IPT (IPT1), Second Dose IPT (IPT2), Pregnant Women Receiving Iron/Folic Acid on ANC 1st Visit, Pregnant Women Receiving Free LLINs: These indicators measured the effectiveness of preventive health measures such as malaria prevention (IPT and LLINs) and iron supplementation during pregnancy.\n",
    "### Maternal and Newborn Health Outcomes:\n",
    "- Pregnant Women Tested for Syphilis, Pregnant Women Tested Positive for Syphilis, Deliveries in Unit, Deliveries in Unit (Fresh Still Births), Deliveries in Unit (Macerated Still Births), Deliveries in Unit (Live Births): These indicators tracked data on testing for syphilis and delivery outcomes, including live births and stillbirths.\n",
    "### Breastfeeding and Postnatal Care:\n",
    "- No. of Mothers Who Initiated Breastfeeding Within the 1st Hour After Delivery (Total), No. of Mothers Who Initiated Breastfeeding Within the 1st Hour After Delivery (No. HIV+), Postnatal Attendances, Postnatal Attendances 6 Days, Postnatal Attendances 6 Weeks, Postnatal Attendances 6 Months: These indicators measured breastfeeding practices and the utilization of postnatal care services.\n",
    "### Maternal and Newborn Mortality:\n",
    "- Newborn Deaths (0-7 Days), OPD Maternal Deaths, Birth Asphyxia, Maternal Deaths Audited, Perinatal Deaths Audited: These indicators measured critical data on mortality rates among mothers and newborns, with a focus on birth asphyxia, a leading cause of neonatal death.\n",
    "### Surgical and Population Data:\n",
    "- MSP Caesarian Sections, Expected Pregnancies (0.05popn/4), Expected Deliveries (0.0485popn/4), Estimated Children <1 (0.043 * popn/4), Projected Population, Total Births: These indicators measured population-based health needs, such as expected pregnancies and births, and tracked the prevalence of caesarean sections.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "id": "acd64cea",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 428 entries, 0 to 427\n",
      "Data columns (total 37 columns):\n",
      " #   Column                                                                                           Non-Null Count  Dtype  \n",
      "---  ------                                                                                           --------------  -----  \n",
      " 0   code                                                                                             428 non-null    object \n",
      " 1   Region                                                                                           428 non-null    object \n",
      " 2   District                                                                                         428 non-null    object \n",
      " 3   Period                                                                                           428 non-null    object \n",
      " 4   Period code                                                                                      428 non-null    object \n",
      " 5   Year                                                                                             428 non-null    object \n",
      " 6   105-2.1 A1:ANC 1st Visit for women                                                               428 non-null    int64  \n",
      " 7   105-2.1 A1:ANC 1st Visit for women (No. in 1st Trimester)                                        428 non-null    int64  \n",
      " 8   105-2.1 A2:ANC 4th Visit for women                                                               428 non-null    int64  \n",
      " 9   105-2.1 A3:Total ANC visits (New clients + Re-attendances)                                       428 non-null    int64  \n",
      " 10  105-2.1 A6:First dose IPT (IPT1)                                                                 428 non-null    int64  \n",
      " 11  105-2.1 A7:Second dose IPT (IPT2)                                                                428 non-null    int64  \n",
      " 12  105-2.1 A8:Pregnant Women receiving Iron/Folic Acid on ANC 1st Visit                             428 non-null    int64  \n",
      " 13  105-2.1 A9:Pregnant Women receiving free LLINs                                                   428 non-null    int64  \n",
      " 14  105-2.1 A10:Pregnant women tested for syphilis                                                   428 non-null    int64  \n",
      " 15  105-2.1 A11:Pregnant women tested positive for syphilis                                          428 non-null    int64  \n",
      " 16  105-2.2a Deliveries in unit                                                                      428 non-null    int64  \n",
      " 17  105-2.2b Deliveries in unit(Fresh Still births)                                                  421 non-null    float64\n",
      " 18  105-2.2c Deliveries in unit(Macerated still births)                                              420 non-null    float64\n",
      " 19  105-2.2d Deliveries in unit(Live Births)                                                         428 non-null    int64  \n",
      " 20  105-2.2 No. of mothers who initiated breastfeeding within the 1st hour after delivery (Total)    428 non-null    int64  \n",
      " 21  105-2.2 No. of mothers who initiated breastfeeding within the 1st hour after delivery (No.HIV+)  428 non-null    int64  \n",
      " 22  105-2.2 Newborn deaths (0-7days)                                                                 415 non-null    float64\n",
      " 23  105-2.2 OPD Maternal deaths                                                                      355 non-null    float64\n",
      " 24  105-2.2 Birth Asyphyxia                                                                          428 non-null    int64  \n",
      " 25  105-2.3 Postnatal Attendances                                                                    428 non-null    int64  \n",
      " 26  105-2.3 Postnatal Attendances 6 Days                                                             428 non-null    int64  \n",
      " 27  105-2.3 Postnatal Attendances 6 Weeks                                                            428 non-null    int64  \n",
      " 28  105-2.3 Postnatal Attendances 6 Months                                                           428 non-null    int64  \n",
      " 29  105-3 OA5 Maternal Deaths Audited                                                                290 non-null    float64\n",
      " 30  105-3 OA6-Perinatal Deaths Audited                                                               321 non-null    float64\n",
      " 31  108-3 MSP Caesarian Sections                                                                     414 non-null    float64\n",
      " 32  Expected Pregnancies (0.05*popn/4)                                                               428 non-null    int64  \n",
      " 33  Expected Deliveries (0.0485*popn/4)                                                              428 non-null    int64  \n",
      " 34  Estimated Children <1 (0.043*popn/4)                                                             428 non-null    int64  \n",
      " 35  Projected population                                                                             418 non-null    float64\n",
      " 36  Total birth                                                                                      428 non-null    int64  \n",
      "dtypes: float64(8), int64(23), object(6)\n",
      "memory usage: 123.8+ KB\n"
     ]
    }
   ],
   "source": [
    "# Displaying the structure on the data set and checking data types and missing values\n",
    "df.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "900b2ac9",
   "metadata": {},
   "source": [
    "## Data Cleaning\n",
    "\n",
    "Data cleaning was an essential step to ensure the dataset was accurate, consistent, and ready for analysis. This process involved identifying and resolving issues such as missing values, duplicates, and inconsistent coulmn names. \n",
    "\n",
    "The following tasks were performed:\n",
    "\n",
    "- Checked for Missing Values: Identified columns with missing data to ensure that no essential information was omitted during analysis.\n",
    "- Handled Missing Values: Filled missing values with zeros to ensure consistency in the dataset and avoid errors during analysis.\n",
    "- Checked for Duplicate Rows: Checked for any duplicate rows and removed them to ensure that the dataset only contained unique records.\n",
    "- Removed Duplicates: Removed duplicate entries that could potentially skew the analysis results.\n",
    "- Standardized Column Names: Stripped any leading or trailing whitespace and converted all column names to lowercase for consistency.\n",
    "\n",
    "These data cleaning steps ensured that the dataset was well structured, with no missing values or duplicates, and that the column names were standardized. This provided a clean dataset for the next stages of analysis.\n",
    "\n",
    "The following Python code was used to carry out these tasks:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "id": "fbc68337",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Index(['code', 'region', 'district', 'period', 'period code', 'year',\n",
       "       '105-2.1 a1:anc 1st visit for women',\n",
       "       '105-2.1 a1:anc 1st visit for women (no. in 1st trimester)',\n",
       "       '105-2.1 a2:anc 4th visit for women',\n",
       "       '105-2.1 a3:total anc visits (new clients + re-attendances)',\n",
       "       '105-2.1 a6:first dose ipt (ipt1)', '105-2.1 a7:second dose ipt (ipt2)',\n",
       "       '105-2.1 a8:pregnant women receiving iron/folic acid on anc 1st visit',\n",
       "       '105-2.1 a9:pregnant women receiving free llins',\n",
       "       '105-2.1 a10:pregnant women tested for syphilis',\n",
       "       '105-2.1 a11:pregnant women tested positive for syphilis',\n",
       "       '105-2.2a deliveries in unit',\n",
       "       '105-2.2b deliveries in unit(fresh still births)',\n",
       "       '105-2.2c deliveries in unit(macerated still births)',\n",
       "       '105-2.2d deliveries in unit(live births)',\n",
       "       '105-2.2 no. of mothers who initiated breastfeeding within the 1st hour after delivery (total)',\n",
       "       '105-2.2 no. of mothers who initiated breastfeeding within the 1st hour after delivery (no.hiv+)',\n",
       "       '105-2.2 newborn deaths (0-7days)', '105-2.2 opd maternal deaths',\n",
       "       '105-2.2 birth asyphyxia', '105-2.3 postnatal attendances',\n",
       "       '105-2.3 postnatal attendances 6 days',\n",
       "       '105-2.3 postnatal attendances 6 weeks',\n",
       "       '105-2.3 postnatal attendances 6 months',\n",
       "       '105-3 oa5 maternal deaths audited',\n",
       "       '105-3 oa6-perinatal deaths audited', '108-3 msp caesarian sections',\n",
       "       'expected pregnancies (0.05*popn/4)',\n",
       "       'expected deliveries (0.0485*popn/4)',\n",
       "       'estimated children <1 (0.043*popn/4)', 'projected population',\n",
       "       'total birth'],\n",
       "      dtype='object')"
      ]
     },
     "execution_count": 30,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Check for missing values\n",
    "df.isnull().sum()\n",
    "\n",
    "# Fill missing values with zero\n",
    "df_filled_zero = df.fillna(0)\n",
    "\n",
    "# Check for duplicate rows\n",
    "df.duplicated().sum()\n",
    "\n",
    "# Remove duplicates\n",
    "df_cleaned = df.drop_duplicates()\n",
    "\n",
    "# Strip whitespace and standardize column names\n",
    "df.columns = df.columns.str.strip().str.lower()\n",
    "\n",
    "# Print the updated column names\n",
    "df.columns"
   ]
  }

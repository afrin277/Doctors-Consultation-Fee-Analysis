<<<<<<< HEAD
Doctor's Consultation Fee Analysis
An Exploratory Data Analysis (EDA) project that analyzes doctor consultation fees across different medical specializations and cities in India using data collected from Practo.

The project focuses on understanding consultation-fee patterns, city-wise and specialization-wise pricing differences, the relationship between experience and consultation fees, patient ratings, premium pricing, and fee segmentation.

📌 Project Overview
Healthcare consultation fees can vary considerably depending on factors such as medical specialization, city, doctor experience, and other market characteristics.

This project analyzes a dataset of 1,080 doctors to identify pricing patterns and generate data-driven insights into doctor consultation fees.

The project follows a structured data pipeline:

Web Scraping → Data Consolidation → Data Cleaning → Analytical Preparation → Exploratory Data Analysis

🎯 Objectives
The main objectives of this project are to:

Analyze the overall distribution of doctor consultation fees.
Compare consultation fees across different cities.
Compare pricing between Metro and Non-Metro cities.
Analyze consultation fees across medical specializations.
Examine the relationship between doctor experience and consultation fees.
Examine the relationship between patient ratings and consultation fees.
Identify premium-priced cities and specializations.
Segment paid consultation fees into Budget, Mid-range, and Premium categories.
Generate business-oriented insights from the observed pricing patterns.
📊 Dataset
The final analysis-ready dataset contains:

1,080 doctor records
9 columns
9 medical specializations
12 cities
2 city tiers: Metro and Non-Metro
1 data source: Practo
Dataset Columns
Column	Description
Doctor_Name	Name of the doctor
Specialization	Medical specialization
Experience	Doctor's experience
Hospital_Name	Hospital/clinic name
City	City where the doctor practices
City_Tier	Metro or Non-Metro classification
Patient_Rating(%)	Patient rating/like percentage
Source	Source of the data
Consultation_Fee(₹)	Doctor consultation fee in Indian Rupees
🗂️ Project Structure
Doctor's_Consultation_Fee_Analysis/
│
├── data/
│   ├── raw/
│   │   └── practo_raw_data.csv
│   │
│   └── processed/
│       ├── practo_cleaned_data.csv
│       └── practo_analysis_data.csv
│
├── notebooks/
│   ├── 01_data_extraction.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_exploratory_data_analysis.ipynb
│
├── presentation/
│   └── doctor_consultation_fee_analysis.pptx
│
├── README.md
├── requirements.txt
├── LICENSE
└── .gitignore
🔄 Data Processing Pipeline
1. Data Extraction
Doctor information was collected from Practo using web scraping techniques with:

Python
Requests
BeautifulSoup
The extraction workflow was designed around multiple medical specializations and cities.

The historical project dataset was consolidated to create the project-level raw dataset containing 1,080 records.

2. Data Cleaning
The raw dataset contained data-quality issues such as:

Missing patient-rating values
Percentage symbols in rating values
"Free Consultation" values in the consultation-fee column
Inconsistent hospital-name formatting
A misspelled column name
The cleaning process included:

Removing % from patient-rating values.
Converting patient ratings into numeric values.
Handling missing patient ratings using the median.
Converting "Free Consultation" into a fee of ₹0.
Converting consultation fees into numeric values.
Standardizing hospital names.
Checking for duplicate records.
Detecting consultation-fee outliers using the IQR method.
Outlier Handling
Consultation-fee outliers were identified but not removed from the main analysis dataset.

This was an intentional decision because a statistically high consultation fee may represent a legitimate market observation rather than an erroneous record.

An outlier-excluded dataset was therefore used only for sensitivity analysis where appropriate.

3. Analytical Preparation
After cleaning, the dataset was prepared for analysis by:

Standardizing column names.

Creating the City_Tier feature.

Classifying six cities as Metro:

Hyderabad
Bangalore
Chennai
Kolkata
Mumbai
Delhi
Classifying the remaining cities as Non-Metro.

The resulting dataset is:

practo_analysis_data.csv

📈 Exploratory Data Analysis
The EDA was performed using:

Pandas
NumPy
Matplotlib
Seaborn
Areas Covered
Overall Consultation Fee
The overall consultation-fee distribution was analyzed using descriptive statistics and visualizations.

Key observations:

Average consultation fee: ₹829.35
Median consultation fee: ₹800
Minimum consultation fee: ₹0
Maximum consultation fee: ₹4,000
Free consultations: 27
IQR-based fee outliers: 39
The mean being slightly higher than the median indicates a right-skewed fee distribution, with higher-fee observations pulling the average upward.

City-Wise Pricing
Consultation fees were compared across all 12 cities.

Highest Average Fee
Mumbai — ₹1,478.89

Lowest Average Fee
Patna — ₹515.00

The analysis also examined fee distributions within individual cities rather than relying only on average values.

Metro vs Non-Metro
The analysis compared consultation fees between Metro and Non-Metro cities.

City Tier	Average Fee	Median Fee
Metro	₹968.70	₹900
Non-Metro	₹690.00	₹700
The observed average difference is:

₹278.70

The results indicate an observed association between city tier and consultation pricing within this dataset.

Specialization-Wise Pricing
Average consultation fees were compared across nine medical specializations.

Specialization	Average Fee
Cardiologist	₹1,016.25
Neurologist	₹991.25
General Surgeon	₹866.67
Orthopedist	₹859.58
General Physician	₹858.75
Dermatologist	₹839.58
ENT	₹814.17
Gynecologist	₹792.50
Dentist	₹425.40
Key Observation
Cardiologist has the highest average consultation fee.
Dentist has the lowest average consultation fee.
Fee distributions and variability were also examined across specializations.

Experience vs Consultation Fee
The relationship between doctor experience and consultation fee was examined using Pearson correlation and regression-based visualization.

Pearson correlation: 0.142

This indicates a weak positive association between experience and consultation fee in the dataset.

The relationship is not strong enough to suggest that experience alone explains consultation pricing.

Correlation indicates association, not causation.

Patient Rating vs Consultation Fee
The relationship between patient rating and consultation fee was also examined.

Pearson correlation: -0.133

This indicates a weak negative association between patient rating and consultation fee in this dataset.

The relationship is weak, so patient rating alone does not explain consultation pricing.

Correlation indicates association, not causation.

💰 Premium Pricing Analysis
Premium pricing was analyzed using the 75th percentile of consultation fees as the threshold.

Premium Fee Threshold
₹1,000

A consultation fee of ₹1,000 or above was classified as premium for this analysis.

Premium-priced records: 365
Share of records: 33.8%
Premium pricing was analyzed at three levels:

City
Specialization
City × Specialization
Key Observations
Mumbai has the highest share of premium-priced consultations among the cities.
Neurology has the highest premium-priced share among the specializations.
Premium pricing patterns vary across city-specialization combinations.
These premium categories are relative to this dataset and should not be interpreted as an industry-wide pricing standard.

🏷️ Fee Segmentation
Paid consultations were segmented into three relative pricing categories using quantile-based segmentation:

Budget
Mid-range
Premium
Free consultations were excluded from this analysis because ₹0 represents a different pricing condition and would distort paid-fee segmentation.

The segmentation is intended to describe relative price positioning within the dataset rather than define universal healthcare pricing bands.

🔎 Key Findings
The major findings from the analysis are:

The overall consultation-fee distribution is right-skewed, with a median fee of ₹800 and an average of ₹829.35.

Mumbai has the highest average consultation fee at ₹1,478.89, while Patna has the lowest at ₹515.00.

Metro cities have a higher average consultation fee than Non-Metro cities in this dataset.

Cardiologists have the highest average consultation fee among the analyzed specializations, while dentists have the lowest.

Doctor experience has only a weak positive association with consultation fees, with a Pearson correlation of 0.142.

Patient rating has a weak negative association with consultation fees, with a Pearson correlation of -0.133.

High-fee observations have a noticeable effect on the overall average, which is why outlier sensitivity analysis was included without removing legitimate observations from the main dataset.

Premium pricing varies substantially across cities, specializations, and their combinations.

💡 Business Insights
The analysis suggests several potential business-level observations:

Location appears to be an important pricing dimension, with Metro cities showing higher average consultation fees than Non-Metro cities.

Medical specialization is associated with substantial pricing differences, indicating that consultation pricing varies considerably across specialties.

Premium pricing is concentrated in certain markets, particularly in cities and specializations with higher average fees.

Experience alone does not explain consultation pricing, suggesting that other factors may contribute to observed fee differences.

Patient rating shows only a weak relationship with consultation fees, indicating that higher consultation fees cannot be directly interpreted as a result of higher patient ratings.

These insights describe patterns observed in the project dataset and should not be interpreted as causal conclusions.

🛠️ Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Requests
BeautifulSoup
Jupyter Notebook
Git & GitHub
▶️ How to Run the Project
1. Clone the repository
git clone <repository-url>
cd Doctor's_Consultation_Fee_Analysis
2. Install dependencies
pip install -r requirements.txt
3. Run the notebooks in order
01_data_extraction.ipynb
        ↓
02_data_cleaning.ipynb
        ↓
03_exploratory_data_analysis.ipynb
The notebooks are designed as a sequential data-processing workflow.

The extraction notebook includes a controlled live-scraping demonstration. The historical project dataset should not be overwritten by running a full live extraction against the current website.

📌 Important Note
This project is intended for educational and portfolio purposes.

The dataset represents the data collected and processed for this project and should not be considered a complete or current representation of Practo's entire doctor database or the current healthcare consultation-fee market.

The analysis identifies patterns and associations within the available dataset; it does not establish causal relationships.


=======
# afrin277-Doctors-Consultation-Fee-Analysis
Exploratory Data Analysis of Doctor Consultation Fees using Python and Pandas.
>>>>>>> origin/main

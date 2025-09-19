# Data Cleaning Project: Layoffs Dataset

This repository contains SQL scripts for cleaning and standardizing a dataset of company layoffs. The goal is to remove duplicates, standardize data formats, handle missing values, and prepare the dataset for analysis.

---
Table of Contents
[Project Overview](#project-overview)
[Database Setup](#database-setup)
[Data Cleaning Steps](#data-cleaning-steps)
[1. Removing Duplicates](#1-removing-duplicates)
[2. Standardizing Data](#2-standardizing-data)
[3. Handling Missing Values](#3-handling-missing-values)


---

## Project Overview
The dataset contains information about company layoffs, including:
- Company name
- Location
- Industry
- Total number of employees laid off
- Percentage of workforce laid off
- Date of layoffs
- Funding stage
- Country
- Funds raised in millions

The SQL scripts in this repository clean the data for easier analysis and reporting.

---

Data Cleaning Steps:

1. Removing Duplicates:
a- Create a staging table based on the original layoffs table.
b- Use ROW_NUMBER() with PARTITION BY to identify duplicate rows.
c- Insert the data into a new staging table including the row number.
d- Delete rows where row_num > 1.

2. Standardizing Data:
a- Remove leading/trailing spaces from company names.
b- Standardize industry names (e.g., Crypto% → Crypto).
c- Remove trailing periods from country names.
d- Convert date strings to DATE format.
e- Replace empty strings in industry with NULL.
f- Propagate industry information from rows with values to rows where it’s missing.

3. Handling Missing Values:
Remove rows where both total_laid_off and percentage_laid_off are NULL.

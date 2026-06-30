# Fair Lending Analysis — DMV Region Home Purchase Loans (2023 HMDA Data)

## Overview
This project analyzes mortgage approval patterns across race, sex, and geography in the DC, Maryland, and Virginia (DMV) region using Home Mortgage Disclosure Act (HMDA) data. The goal is to surface disparities in loan approval outcomes and loan amounts across demographic groups.

## Data Source
- **Source:** FFIEC HMDA Platform (ffiec.cfpb.gov)
- **Year:** 2023
- **Scope:** DC, Maryland, Virginia
- **Filter:** Home purchase loans only

## Tools
- **Python (pandas)** — data cleaning and exploratory data analysis
- **Tableau Public** — visualization and dashboard

## Process
1. Downloaded individual state-level CSVs for DC, MD, and VA and combined them into a single dataframe (542,099 rows, 99 columns)
2. Selected relevant columns for analysis (interest rate, loan-to-value ratio, debt-to-income ratio, property value, income, loan term, applicant sex, state, county, credit score type, submission method, derived race, loan type, action taken, loan purpose, loan amount)
3. Dropped rows with nulls in low-null columns (county code, loan term)
4. Decoded HMDA's numeric codes into human-readable labels (action taken, applicant sex)
5. Filtered to home purchase loans (loan_purpose == 1) and then to approved/denied outcomes only, producing a final analysis dataset of 188,445 rows
6. Calculated summary statistics: approval/denial rate by race, by sex, by state; mean loan amount by race
7. Exported summary tables to CSV for visualization in Tableau

## Key Findings
- **Race:** Black or African American (18.6%) and American Indian or Alaska Native (20.8%) applicants are denied at roughly double the rate of White (9.2%) and Asian (10.9%) applicants
- **Sex:** A smaller but present gap exists — female applicants are denied at 12.8% versus 10.9% for male applicants
- **Loan amount:** Asian ($492K) and Joint ($497K) applicants receive notably higher average loan amounts than Black or African American ($356K) and American Indian or Alaska Native ($316K) applicants
- **Geography:** Minimal variation in approval rates across DC (89.8%), Maryland (88.4%), and Virginia (88.1%)

## Dashboard
https://public.tableau.com/app/profile/marc.avery/viz/HomeLoan_17828552146910/Dashboard1#2

## Files
- `DMVLoan.ipynb` — Python cleaning and EDA notebook
- `Chart(CSV)/` — exported summary CSVs used for Tableau
- `Home Loan.twb` — Tableau workbook (.twbx)

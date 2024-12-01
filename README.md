# Loan-Insights-Project

## Introduction
This project involves cleaning, transforming and preparing loan-related data for EasyLoan, a financial services provider offering personal loans, car loans and mortgages. The goal is to ensure data accessibility and reliability for the analytics team to identify areas of strength and weakness across geographic regions (USA, UK and Canada).

## Project Objectives:
Clean and standardize client data for accurate reporting and analysis.
Fill missing values in critical data fields (e.g., repayment channels) based on defined business rules.
Prepare data for monitoring active policy holders, including counts and categorizations by policy type.

## Database Schema
The project utilizes the lending database, which consists of the following key tables:
client: Stores details about clients, including date of birth, employment status, and country.
repayment: Tracks repayment details, including repayment amount and channel.
policy: Contains information about active loan policies and their types.
![image](https://github.com/user-attachments/assets/c753c404-bc13-4873-a42f-3c144f08b037)


## Tasks
Task 1: Cleaning and Standardizing the client Table
The client table required the following transformations:
Convert the date_of_birth column from formats like Month DD, YYYY to YYYY-MM-DD while ensuring it remains a DATE type.
Standardize employment_status to be either employed or unemployed, ignoring case or inconsistent labels like Full-time or Part-time.
Ensure the country column values are uppercased and limited to valid entries: USA, UK, or CA.

Task 2: Handling Missing Values in the repayment Table
Some repayment_channel values were missing. Business rules were provided to infer the channel:
Repayments > 4000: Use bank account.
Repayments < 1000: Use mail.

Task 3: Monitoring Active Policies by Policy Type
To help the sales team monitor active loan policies, the task required grouping and counting policies by type.

## Challenges Faced
Date Parsing Issues:
The date_of_birth column stored dates in a non-standard format (Month DD, YYYY).
Solution: Using TO_CHAR and TO_DATE with ::timestamp casting ensured correct formatting.

Data Cleaning Consistency:
Employment statuses had inconsistent labels like Full-time or Emplouyed.
Solution: A CASE statement with LOWER() normalized these values.

Handling Missing Values:
Missing repayment_channel values required logical inference.
Solution: Implemented COALESCE and CASE for defaulting based on repayment amounts.

## Conclusion
This project highlights the importance of thorough data preparation for downstream analytics. By ensuring data quality, we empower the analytics team to deliver actionable insights for EasyLoan's business strategy.

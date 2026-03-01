Case Study: Data Cleaning of Global Layoffs Dataset

Project Title
Data Cleaning and Standardization of Layoffs Dataset Using SQL

Objective
The dataset contained records of company layoffs across industries, countries, and funding stages. However, it suffered from:
• 	Duplicate entries
• 	Inconsistent formatting (extra spaces, trailing characters)
• 	Null or blank values
• 	Non-standard date formats
The objective was to clean and standardize the dataset to ensure accuracy and reliability for downstream analysis.

Approach
1. Remove Duplicates
•	Used ROW_NUMBER() with PARTITION BY to identify duplicate rows
•	Deleted rows where row_num > 1
2. Standardizing Data
•	Trimmed whitespace from company names.
•	Unified industry labels (e.g., “Crypto%” → “Crypto”).
•	Cleaned country names (removed trailing periods, standardized “United States”).
•	Converted string dates (MM/DD/YYYY) into proper SQL DATE type using STR_TO_DATE.
3. Handle Nulls and Blanks
•	Set empty industry values to NULL.
•	Filled missing industries by joining with other rows of the same company.
•	Deleted rows where both total_laid_off and percentage_laid_off were missing.
4. Remove Any Column
•	Deleted the row_num column using ALTER TABLE and DROP COLUMN

Results
•	Removed duplicate records, ensuring unique entries.
•	Standardized company, industry, and country fields for consistency.
•	Converted all dates into proper SQL DATE format.
•	Cleaned nulls and blanks, ensuring the dataset is ready for analysis.

Key Learnings
•	Practical use of window functions (ROW_NUMBER) for deduplication.
•	Importance of string functions (TRIM, LIKE) in text cleaning.
•	Handling null values with joins and conditional updates.
•	Building a repeatable cleaning pipeline for real-world datasets.

Next Steps
•	Perform exploratory data analysis (EDA) on the cleaned dataset.
•	Visualize layoffs trends by industry, country, and funding stage.
•	Share insights in dashboards (Tableau/Power BI) or reports.

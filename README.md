# Data Science Salaries Estimator: Project Overview

 - Created a tool that estimates data science salaries (MAE ~ $ 12K) to help data scientists negotiate their income when they get a job
- Scraped over 1000 job descriptions from glassdoor using python and selenium
- Engineered features from the text of each job description to quantify the value companies put on python, excel, aws, and spark
- Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model

## Code and Resources Used

- Python Version: 3.9
- Packages: pandas, numpy, sklearn, matplotlib, seaborn, selenium, flask, json, joblib
- For Web Framework Requirements: pip install -r requirements.txt
- Scraper Github: https://github.com/arapfaik/scraping-glassdoor-selenium
- Scraper Article: https://towardsdatascience.com/selenium-tutorial-scraping-glassdoor-com-in-10-minutes-3d0915c6d905

## Web Scraping

Tweaked the web scraper github repo (mentioned above) to scrape 1000 job postings from glassdoor.com. With each job, we got the following:

- Job title
- Salary Estimate
- Job Description
- Rating
- Company
- Location
- Company Headquarters
- Company Size
- Company Founded Date
- Type of Ownership
- Industry
- Sector
- Revenue
- Competitors

## Data Cleaning

The second step after scraping the data was to clean the data so that it could be usable for model implementation. The following changes were made o the data:

- Extracted the numeric data from the salary
- Made seperate columns for employer provided salar and the hourly wages
- Removed the rows entirely which did not have any salary values
- Parsed rating out of company text
- Made a new column for company state
- Made another column to mention if the job was in the headquaters
- Made another column for the age of the company by using the founded date from teh company
- Created columns mentionin the skills that were required for a particular role provided by the company in the job description:
  - Python
  - R
  - Excel
  - AWS
  - Spark
- Column for simplified job title and Seniority
- Column for description length

## EDA

Analyzed the distribution of the data and the value counts for various categorical variables.  Below are the few insights:

## Model Building 

The categorical variables were transformed into the dummy variables. the data was split into train and test daat sets with a test size of 20%

Three different models were implemented and evaluated by using Mean Absolute Error and Root Mean Squared Error

The models used are:
- **Multiple Linear Regression** - Baseline for the model
- **Lasso Regression** - Becasue of the data being sparsed from various categorical variables. Normalized regression like Lasso would be more effective in this situation
- **Random Forest** - This would be a good fit because of the sparsity associated with the data

## Model Performance


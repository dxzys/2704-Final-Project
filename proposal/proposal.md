# Project Proposal
## Cameron Steeves, Andrew Savoie, Hongbo Li
## November 2025

---

# 1. Introduction and Topic
This is a project proposal for the final project in the course CS2704 Data Analytics using Python. Our project examines the relationship between generative AI and employment trends in the United States. As artificial intelligence technologies rapidly advance, concerns have emerged about their impact on professional occupations, particularly among recent college graduates entering knowledge-based fields. This analysis aims to quantify the relationship between AI exposure levels across occupations and observed changes in employment patterns.

---

# 2. Hypothesis
**Occupations with higher exposure to generative AI technologies demonstrate measurable increases in unemployment rates and decreases in job postings among white collar workers in the United States.**

## 2.1 Methodology
To test our hypothesis, we will combine employment data from multiple sources and analyze how AI-exposed occupations have fared over the past decade compared to those less affected by AI technologies. Our approach starts by organizing a dataset that links each occupation to its AI exposure level and tracks employment patterns from 2014 to 2024. We will group occupations into high, medium, and low AI-exposure categories and compare their trends over time. This will let us visualize changes in employment, unemployment rates, and job postings across the groups. We will focus on how recent college graduates and entry-level jobs have been hit, since they might be the most at risk from AI shifts.
Ideally, we will be able to quantify the relationship between AI exposure and employment outcomes by building predictive, which will help us determine whether AI-exposure is a significant predictor of employment changes and project how these trends might continue into the future.

---

# 3. Databases

## O\*NET-SOC Occupational Data  
We use the **O\*NET 30.0 Database** for standardized occupation descriptions and SOC codes.  
Source: O\*NET Resource Center – Database page  
<https://www.onetcenter.org/database.html#individual-files>

We use this dataset to:
- identify white-collar occupations  
- classify each job consistently  
- merge BLS data and AI-exposure scores by SOC code  

---

## AI Exposure Metrics (OpenAI GPT Exposure Scores)  
We use the **GPTs-are-GPTs occupational exposure data** from OpenAI’s GitHub repository:  

**Download:** data/occ_level.csv  
Direct link: https://github.com/openai/GPTs-are-GPTs/blob/main/data/occ_level.csv


We use this dataset to:
- label each occupation as **High / Medium / Low AI exposure**  
- compare employment trends across these exposure categories  
- use exposure level as the **independent variable** in our statistical tests  

---

## Bureau of Labor Statistics (BLS) Employment Data
We use BLS programs that provide employment outcomes from 2014–2024:

- **OEWS – Occupational Employment and Wage Statistics**  
  Program page: <https://www.bls.gov/oes/tables.htm>  
  Used for employment counts and wage levels by occupation.

  **Download:** “All data (XLSX)” file for each year (2014–2024)


- **JOLTS – Job Openings and Labor Turnover Survey**  
  Data page: <https://www.bls.gov/jlt/data.htm>  
  Used for national trends in job demand (job openings), hiring, and separations.

  Because JOLTS provides each measure as a separate data series, we download
  **three individual time-series tables** using the JOLTS One-Screen Data Tool:

  - Job Openings (Total Nonfarm, Total US)  
  - Hires (Total Nonfarm, Total US)  
  - Total Separations (Total Nonfarm, Total US)  

  Each series is exported as an Excel file from the One-Screen tool and imported
  into Python using `pandas`. We then convert the monthly values into annual
  averages (2014–2024) and merge them with our occupation-level dataset by year.


- **CPS – Current Population Survey**  
  Data tables page: <https://www.bls.gov/cps/tables.htm>  
  Used for unemployment rates by education level, focusing on workers with a
  bachelor's degree or higher (proxy for white-collar and recent graduates).

  We download the **Annual Averages – Table A-4 (Employment status of the civilian
  population 25 years and over by educational attainment)** for each year **2014–2023**.  
  CPS annual tables only extend to 2023 because 2024 annual averages have not yet
  been released. These tables are downloaded in XLSX format and imported into
  Python using `pandas`.

We use BLS data to measure:
- employment growth or decline  
- unemployment levels  
- job demand and hiring patterns  

---

# 4. Expected Results
We expect finding a statistically significant negative correlation between AI exposure levels and employment growth in white collar occupations. Specifically, high AI-exposure occupations will show greater employment volatility compared to low-exposure roles over the past few years. We believe that there is a noticeable impact that the rise of generative AI has on the job market, particularly beginning with the launch of ChatGPT in late 2022.

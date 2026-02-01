# Skills & Salary Analysis

## Overview

An analysis exploring the relationship between skills, salaries, and job roles in the data science market. Built using Power Query, Power Pivot, DAX, and Pivot Charts to answer practical questions about what skills lead to higher pay.

### Project File

📁 [Skills_Salary_Analysis.xlsx](Skills_Salary_Analysis.xlsx)

## Questions Explored

1. Do more skills get you better pay?
2. What's the salary difference between US and international roles?
3. What are the most in-demand skills for data professionals?
4. What's the pay associated with the top 10 skills?

## Excel Skills Used

- **Power Query** - ETL (Extract, Transform, Load)
- **Power Pivot** - Data modeling and relationships
- **DAX** - Custom measures and calculations
- **Pivot Tables** - Aggregation and analysis
- **Pivot Charts** - Visualization

---

## 1. Do More Skills Get You Better Pay?

### Power Query (ETL Process)

**Extract:** Pulled data from source file into two queries:
- `data_jobs_all` - Job postings with titles, salaries, locations
- `data_job_skills` - Skills listed for each job ID

**Transform:** 
- Changed column types
- Removed unnecessary columns
- Cleaned text and trimmed whitespace

![Transform Jobs](/0_Resources/Images/2_Project_Analysis_Screenshot1.png)

![Transform Skills](/0_Resources/Images/2_Project_Analysis_Screenshot2.png)

**Load:** Loaded both queries into the workbook for analysis.

### Analysis

![Skills vs Salary Chart](/0_Resources/Images/2_Project_Analysis_Chart1.png)

**Findings:**
- Positive correlation between number of skills requested and median salary
- Senior Data Engineer and Data Scientist roles require more skills AND pay more
- Business Analyst roles require fewer skills and offer lower salaries

**Takeaway:** Investing in multiple relevant skills pays off, especially for senior roles.

---

## 2. US vs International Salaries

### Pivot Tables & DAX

Created a PivotTable from the data model with a DAX measure to filter US-only salaries:

```dax
US Median Salary := 
CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States"
)
```

Basic median measure for comparison:

```dax
Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
```

### Analysis

![US vs International](/0_Resources/Images/2_Project_Analysis_Chart2.png)

**Findings:**
- US salaries are consistently higher across all roles
- The gap is largest for senior/specialized positions
- Data Scientist and Senior Data Engineer see the biggest US premium

**Takeaway:** Location matters significantly for salary expectations and negotiations.

---

## 3. Top Skills for Data Professionals

### Power Pivot Data Model

Created a relationship between the two tables using `job_id`:

![Data Model](/0_Resources/Images/2_Project_Analysis_Screenshot5.png)

This allows analysis across both job information and skills in a single pivot table.

### Analysis

![Top Skills](/0_Resources/Images/2_Project_Analysis_Chart3.png)

**Findings:**
- SQL and Python dominate across all data roles
- Cloud platforms (AWS, Azure) show strong demand
- Excel remains relevant, especially for analyst roles
- Visualization tools (Tableau, Power BI) are consistently requested

**Takeaway:** SQL and Python are non-negotiable foundations. Cloud skills are increasingly important.

---

## 4. Pay for Top 10 Skills

### Pivot Chart (Combo Chart)

Created a combo chart plotting:
- **Primary Axis:** Median salary (clustered column)
- **Secondary Axis:** Skill likelihood/frequency (line with markers)

### Analysis

![Skills Pay Chart](/0_Resources/Images/2_Project_Analysis_Chart4.png)

**Findings:**
- Python, Oracle, and SQL are associated with highest median salaries
- Cloud skills (AWS, Azure) also correlate with higher pay
- PowerPoint and Word have lowest salaries and demand
- High-frequency skills (SQL, Python) also tend to be high-paying

**Takeaway:** Focus learning time on Python, SQL, and cloud platforms for the best salary ROI.

---

## Key Takeaways

1. **More skills = higher pay**, especially in senior roles
2. **US roles pay 20-40% more** than international equivalents
3. **SQL and Python are essential** - appear in most postings and correlate with higher salaries
4. **Cloud skills are growing** - AWS and Azure show strong demand and good pay
5. **Soft skills (PowerPoint, Word) don't drive salary** - focus on technical skills

---

## What I Learned

- Power Query makes data cleaning repeatable and documented
- Power Pivot relationships eliminate the need for VLOOKUP across tables
- DAX measures are more flexible than standard pivot table calculations
- Combo charts effectively show two related metrics together

---

## Contact

**Davis Rapp**  
[LinkedIn](https://linkedin.com/in/davis-rapp-2b7167128) | [GitHub](https://github.com/drapp3)
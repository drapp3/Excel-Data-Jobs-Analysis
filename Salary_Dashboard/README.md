# Excel Salary Dashboard

![Dashboard Demo](/0_Resources/Images/1_Salary_Dashboard_Final_Dashboard.gif)

## Overview

An interactive Excel dashboard for exploring data science salaries by job title, country, and schedule type. Built to practice array formulas, conditional logic, and dashboard design.

### Dashboard File

📁 [Salary_Dashboard.xlsx](Salary_Dashboard.xlsx)

## Excel Skills Used

- **Charts** - Bar charts and map visualizations
- **Array Formulas** - MEDIAN with nested IF for multi-criteria filtering
- **Data Validation** - Dropdown menus for user interaction
- **Named Ranges** - For cleaner formula references

## Dataset

Real-world data science job postings from 2023 containing:
- Job titles (Data Analyst, Data Scientist, Data Engineer, etc.)
- Salaries (yearly and hourly)
- Locations (50+ countries)
- Schedule types (Full-time, Part-time, Contract)

---

## Dashboard Components

### Salary by Job Title - Bar Chart

<img src="/0_Resources/Images/1_Salary_Dashboard_Chart1.png" width="850" height="550" alt="Salary Bar Chart">

- Horizontal bar chart comparing median salaries across roles
- Sorted descending for easy comparison
- Senior roles and Engineers show higher pay than Analyst roles

### Country Salaries - Map Chart

![Country Map](/0_Resources/Images/1_Salary_Dashboard_Country_Map.gif)

- Geographic visualization of salary differences
- Color-coded by salary level
- Quick view of high-paying regions (US, Western Europe, Australia)

---

## Key Formulas

### Median Salary Calculation

```excel
=MEDIAN(
    IF(
        (jobs[job_title_short]=A2)*
        (jobs[job_country]=country)*
        (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
        (jobs[salary_year_avg]<>0),
        jobs[salary_year_avg]
    )
)
```

**How it works:**
- Each condition in parentheses returns TRUE/FALSE (1/0)
- Multiplying conditions = AND logic (all must be true)
- `ISNUMBER(SEARCH(...))` allows partial matching for schedule types
- Excludes zero salaries to avoid skewing the median

### Filtering Job Schedule Types

```excel
=FILTER(J2#, (NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#)))) * (J2#<>0))
```

**Purpose:** Creates a clean list of schedule types by removing combined values like "Full-time and Part-time"

---

## Data Validation Setup

<img src="/0_Resources/Images/1_Salary_Dashboard_Data_Validation.gif" width="425" height="400" alt="Data Validation Demo">

Three dropdown menus control the dashboard:
- **Job Title** - Select from 10 data roles
- **Country** - Filter by location
- **Type** - Full-time, Part-time, Contract, etc.

Each dropdown pulls from a filtered/cleaned list to prevent invalid entries.

---

## Insights

1. **Senior roles pay significantly more** - Senior Data Engineer median is ~40% higher than Data Analyst
2. **US salaries lead globally** - Consistently higher across all job titles
3. **Full-time roles dominate** - Most postings and highest salaries are full-time positions

---

## What I Learned

- Array formulas can replace complex SUMPRODUCT or helper columns
- ISNUMBER + SEARCH is useful for partial text matching
- Data validation + named ranges make dashboards user-friendly
- Map charts have limitations (some countries don't map correctly)

---

## Contact

**Davis Rapp**  
[LinkedIn](https://linkedin.com/in/davis-rapp-2b7167128) | [GitHub](https://github.com/drapp3)
---
layout: default
title: About
permalink: /about/
---

<div class="about-header-section">
  <div class="about-profile-picture">
    <img src="/assets/images/Profile Picture.jpg" alt="Justin Wasner">
  </div>
  <div class="about-title">
    <h2>About Me</h2>
  </div>
</div>

## Professional Background

I'm an engineer with a strong foundation in root cause analysis, large data, and data visualization. My work focuses on culminating large data sets, conducting exploratory data analysis (EDA), and creating data-driven dashboards to help solve problems.

My interest in data started with a simple curiosity: I enjoyed spotting patterns and asking “why” things were happening. Over time, that curiosity grew into a skill set across analysis, visualization, and building practical tools that help teams make better decisions. I’m always learning, and I’m excited to keep growing in the field.

My professional background is rooted in manufacturing. Over the past 6+ years, I’ve worked across Aerospace/Defense, Automotive, and highly automated Energy Storage environments. In highly automated settings, I had access to large volumes of production data. It was an ideal “learning lab” where I developed strong fundamentals in advanced Excel, Python, Power BI, data manipulation, data visualization, and working with large datasets.

This interest in data also carried into my free time, where I started using these skills to explore questions I was curious about and to build small tools for practice. A few of the projects in this portfolio reflect that self-driven learning and experimentation outside of work.

## Skills & Expertise

- **Tools & Languages:** Excel (PivotTables, lookups, advanced formulas), Python (pandas, NumPy, scikit-learn, matplotlib), SQL (joins, CTEs, window functions), Power BI (Power Query, DAX), Git/GitHub
- **Analytics:** EDA, statistical analysis (hypothesis testing), KPI definition, time-series analysis, correlation analysis, anomaly detection, data visualization, analytical storytelling
- **Data Prep & Quality:** data wrangling, data quality checks & validation, reproducible analysis
- **Machine Learning:** feature engineering, model training & evaluation (scikit-learn)
- **Data Engineering:** ETL pipelines, data modeling, query optimization, file formats (CSV/Parquet)
- **Web Apps:** Streamlit, Flask, APIs
- **Manufacturing Domain Expertise:** KPI development & review, root cause analysis (RCA), continuous improvement (CI), process mapping/flow understanding, PFMEA, Control Plans (CP), APIS-IQ

## Experience

### Process Engineer

[AESC US](https://us.aesc-group.com/)

Smyrna, TN

*Jul 2021 – Present*

- Built and maintained **Python (pandas) + SQL** pipelines to ingest, clean, validate, and transform high-volume manufacturing/equipment data (**500k+ rows/day**) into analysis-ready datasets (CSV/Parquet).
  - Check out the [Production Data ETL](/projects/Production_Data_ETL/) Project
- Delivered **Power BI dashboards** for manufacturing KPIs (throughput, yield, downtime, utilization), improving stakeholder visibility and decision-making.
- Performed **EDA + root-cause investigations** across production, quality, and equipment data to identify drivers of performance and abnormal behavior.
- Applied **statistical / before-after analysis** to evaluate process changes and communicate operational impact and risk.
- Improved reporting performance through **SQL optimization**, reducing dashboard refresh times by **50%+**.
- Created documentation and mentored teammates on **Python, SQL, and Power BI** to scale analytics adoption.
- Analyzed time-series equipment signals to identify early indicators of degradation/failure.
- Documented data sources, assumptions, and logic in a centralized knowledge base.

### Project Engineer

[Walker Die Casting](https://www.walkerdiecasting.com/)

Lewisburg, TN

*Nov 2020 – Jul 2021*
- Led cross‑functional investigations to identify root causes of low‑profitability products, using structured problem‑solving and data‑driven analysis to guide operational improvements.

### Mechanical Engineer

[Lockheed Martin - Missile and Fire Control (MFC)](https://www.lockheedmartin.com/en-us/who-we-are/business-areas/missiles-and-fire-control.html)

Camden, AR

*Aug 2019 – Nov 2020*

- Designed and optimized production tooling using structured requirements, tolerance analysis, and iterative testing to reduce manufacturing variation and defects.

### Technical Intern

[Northrop Grumman - Aeronautics Systems](https://www.northropgrumman.com/who-we-are/business-sectors/aeronautics-systems/)

Palmdale, CA

*Jun 2018 - Aug 2018*

- Supported tool engineering by tracking task progress, identifying delays, and improving workflow visibility through organized reporting.

## Education

**Bachelor of Science in Mechanical Engineering**  
*Louisiana Tech University* | Graduated: 2019

## Download my Resume!
<div class="resume-section">
  <a href="/assets/resume/resume.pdf" class="btn-resume" download>
    📄 Download My Resume
  </a>
</div>

## Contact Me
<div class="contact-section">
  {% if site.author.email %}<p><strong>Email:</strong> <a href="mailto:{{ site.author.email }}">{{ site.author.email }}</a></p>{% endif %}
  {% if site.author.github %}<p><strong>GitHub:</strong> <a href="https://github.com/{{ site.author.github }}">@{{ site.author.github }}</a></p>{% endif %}
  {% if site.author.linkedin %}<p><strong>LinkedIn:</strong> <a href="https://linkedin.com/in/{{ site.author.linkedin }}">{{ site.author.linkedin }}</a></p>{% endif %}
</div>
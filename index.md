---
layout: default
title: Home
---
Hi, I'm **Justin Wasner**, an engineer specializing in statistical analysis and data visualization. I enjoy building analysis workflows and dashboards that translate messy data into decisions stakeholders can act on.

I'm located in the Nashville metropolitan area and currently exploring opportunities in the data field. If you're looking for someone to support analytics, reporting, or data-driven product work, feel free to reach out; my email and linkedin is linked above.

Take a look at my featured projects below. You can see all of my projects and more about me using the links above.

## Featured Projects

<div class="projects-grid">
  {% assign featured_projects = site.projects | where: "featured", true | sort: 'featured_order' %}
  {% for project in featured_projects %}
  <div class="project-card">
    <h3><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h3>
    {% if project.featured_image %}
    <div class="project-card-image">
      <a href="{{ project.url | relative_url }}">
        <img src="{{ project.featured_image | relative_url }}" alt="{{ project.title }}">
      </a>
    </div>
    {% endif %}
    <p class="project-date">{{ project.date | date: "%B %Y" }}</p>
    <p>{{ project.description }}</p>
    <div class="project-tags">
      {% for tech in project.skills %}
      <span class="tag">{{ tech }}</span>
      {% endfor %}
    </div>
    <a href="{{ project.url | relative_url }}" class="btn-project">View Project →</a>
  </div>
  {% endfor %}
</div>

## About Me

I'm an engineer with a strong foundation in root cause analysis, large data, and data visualization. My work focuses on culminating large data sets, conducting exploratory data analysis (EDA), and creating data-driven dashboards to help solve problems.

### Core Skills:
- **Tools & Languages:** Excel (PivotTables, lookups, advanced formulas), Python (pandas, NumPy, scikit-learn, matplotlib), SQL (joins, CTEs, window functions), Power BI (Power Query, DAX), Git/GitHub
- **Analytics:** EDA, statistical analysis (hypothesis testing), KPI definition, time-series analysis, correlation analysis, anomaly detection, data visualization, analytical storytelling
- **Data Prep & Quality:** data wrangling, data quality checks & validation, reproducible analysis
- **Machine Learning:** feature engineering, model training & evaluation (scikit-learn)
- **Data Engineering:** ETL pipelines, data modeling, query optimization, file formats (CSV/Parquet)
- **Web Apps:** Streamlit, Flask, APIs
- **Manufacturing Domain Expertise:** KPI development & review, root cause analysis (RCA), continuous improvement (CI), process mapping/flow understanding, PFMEA, Control Plans (CP), APIS-IQ

<div class="about-links">
  <a href="/about" class="btn-secondary">Learn More About Me</a>
  <a href="/projects" class="btn-secondary">View All Projects</a>
</div>

## Download Resume

<div class="resume-section">
  <a href="/assets/resume/JustinWasnerResume.pdf" class="btn-resume" download>
    📄 Download My Resume
  </a>
</div>

---

<div class="contact-info">
  <p>Interested in collaboration or have a project in mind? Let's connect!</p>
  <p>
    {% if site.author.github %}<a href="https://github.com/{{ site.author.github }}">GitHub</a>{% endif %}
    {% if site.author.github and site.author.linkedin %} | {% endif %}
    {% if site.author.linkedin %}<a href="https://linkedin.com/in/{{ site.author.linkedin }}">LinkedIn</a>{% endif %}
    {% if site.author.linkedin and site.author.email %} | {% endif %}
    {% if site.author.email %}<a href="mailto:{{ site.author.email }}">Email</a>{% endif %}
  </p>
</div>

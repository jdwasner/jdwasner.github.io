---
layout: default
title: Home
---

# Welcome to My Data Science Portfolio

Hi, I'm **Justin Wasner**, a passionate engineer with a focus in statistical analysis and data visualization. I specialize in turning complex data into actionable insights that drive business decisions.

## Featured Projects

<div class="projects-grid">
  {% assign featured_projects = site.projects | sort: 'date' | reverse | limit: 3 %}
  {% for project in featured_projects %}
  <div class="project-card">
    <h3><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h3>
    <p class="project-date">{{ project.date | date: "%B %Y" }}</p>
    <p>{{ project.description }}</p>
    <div class="project-tags">
      {% for tech in project.technologies %}
      <span class="tag">{{ tech }}</span>
      {% endfor %}
    </div>
    <a href="{{ project.url | relative_url }}" class="btn-project">View Project →</a>
  </div>
  {% endfor %}
</div>

## About Me

I'm an engineer with a strong foundation in root cause analysis, large data, and data visualization. My work focuses on culminating large data sets, conducting exploratory data analysis (EDA), and creating data-driven dashboards to help solve problems.

### Core Competencies:
- **Data Analysis:** Python, SQL, MiniTab, Excel
- **Data Engineering:** ETL Pipelines, Data Modeling, SQL Query Optimization
- **Dashboard Building:** Power BI, FineReport
- **Root Cause Analysis:** 5Why, Fishbone, PFMEA

[Learn More About Me](/about) | [View All Projects](/projects)

## Download Resume

<div class="resume-section">
  <a href="/assets/resume/resume.pdf" class="btn-resume" download>
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

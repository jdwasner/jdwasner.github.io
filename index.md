---
layout: default
title: Home
---

# Welcome to My Data Science Portfolio

Hi, I'm **J.D. Wasner**, a passionate data scientist with expertise in machine learning, statistical analysis, and data visualization. I specialize in turning complex data into actionable insights that drive business decisions.

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

I'm a data scientist with a strong foundation in statistical modeling, machine learning, and data engineering. My work focuses on building predictive models, conducting exploratory data analysis, and creating data-driven solutions for real-world problems.

**Core Competencies:**
- Machine Learning & Deep Learning
- Statistical Analysis & Hypothesis Testing
- Data Visualization & Storytelling
- Python, R, SQL, and Cloud Technologies

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
    <a href="https://github.com/{{ site.author.github }}">GitHub</a> | 
    <a href="https://linkedin.com/in/{{ site.author.linkedin }}">LinkedIn</a> | 
    <a href="mailto:{{ site.author.email }}">Email</a>
  </p>
</div>

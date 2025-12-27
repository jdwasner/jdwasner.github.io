---
layout: default
title: Projects
permalink: /projects/
---

# Data Science Projects

Explore my portfolio of data science and machine learning projects. Each project demonstrates different aspects of data science, from exploratory data analysis to advanced machine learning implementations.

<div class="projects-list">
  {% assign sorted_projects = site.projects | sort: 'date' | reverse %}
  {% for project in sorted_projects %}
  <div class="project-card-full">
    <h2><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h2>
    <p class="project-meta">
      <span class="date">📅 {{ project.date | date: "%B %d, %Y" }}</span>
    </p>
    <p class="project-description">{{ project.description }}</p>
    
    <div class="project-technologies">
      <strong>Technologies:</strong>
      {% for tech in project.technologies %}
      <span class="tag">{{ tech }}</span>
      {% endfor %}
    </div>
    
    <div class="project-links">
      <a href="{{ project.url | relative_url }}" class="btn-project">View Details →</a>
      {% if project.github %}
      <a href="{{ project.github }}" class="btn-secondary" target="_blank">GitHub Repository</a>
      {% endif %}
      {% if project.demo %}
      <a href="{{ project.demo }}" class="btn-secondary" target="_blank">Live Demo</a>
      {% endif %}
    </div>
  </div>
  {% endfor %}
</div>

---

## Project Categories

My projects span multiple domains of data science:

- **Machine Learning:** Classification, regression, and clustering problems
- **Deep Learning:** Neural networks for computer vision and NLP
- **Time Series:** Forecasting and anomaly detection
- **NLP:** Text analysis and natural language understanding
- **Computer Vision:** Image classification and object detection
- **Data Engineering:** ETL pipelines and data processing

{% if site.author.github %}Want to see the code? All projects are available on [GitHub](https://github.com/{{ site.author.github }}).{% endif %}

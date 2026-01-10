---
layout: default
title: Projects
permalink: /projects/
---

# Data Science Projects
Explore my portfolio of data projects. Each project demonstrates different aspects of data from simple plots to advanced regression machine learning implementations.

<!-- Skill Filter -->
<div class="skill-filter">
  <label for="skill-select"><strong>Filter by Skill:</strong></label>
  <select id="skill-select" class="skill-dropdown">
    <option value="all">All Projects</option>
    {% assign all_skills = "" | split: "" %}
    {% for project in site.projects %}
      {% for skill in project.skills %}
        {% unless all_skills contains skill %}
          {% assign all_skills = all_skills | push: skill %}
        {% endunless %}
      {% endfor %}
    {% endfor %}
    {% for project in site.coming_soon_projects %}
      {% for skill in project.skills %}
        {% unless all_skills contains skill %}
          {% assign all_skills = all_skills | push: skill %}
        {% endunless %}
      {% endfor %}
    {% endfor %}
    {% assign sorted_skills = all_skills | sort %}
    {% for skill in sorted_skills %}
    <option value="{{ skill }}">{{ skill }}</option>
    {% endfor %}
  </select>
</div>

<div class="projects-list">
  {% assign sorted_projects = site.projects | sort: 'date' | reverse %}
  {% for project in sorted_projects %}
  <div class="project-card-full" data-skills="{{ project.skills | join: ',' }}">
    <h2><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h2>
    <p class="project-meta">
      <span class="date">📅 {{ project.date | date: "%B %d, %Y" }}</span>
    </p>
    <p class="project-description">{{ project.description }}</p>
    
    <div class="project-skills">
      <strong>Skills:</strong>
      {% for tech in project.skills %}
      <a href="{{ '/projects' | relative_url }}?skill={{ tech | url_encode }}" class="tag">{{ tech }}</a>
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

## Coming Soon

<div class="projects-list coming-soon-section">
  {% for project in site.coming_soon_projects %}
  <div class="project-card-full coming-soon" data-skills="{{ project.skills | join: ',' }}">
    <h2>{{ project.title }}</h2>
    <p class="project-meta">
      <span class="coming-soon-badge">🚧 Coming Soon</span>
    </p>
    <p class="project-description">{{ project.description }}</p>
    
    <div class="project-skills">
      <strong>Skills:</strong>
      {% for tech in project.skills %}
      <a href="{{ '/projects' | relative_url }}?skill={{ tech | url_encode }}" class="tag">{{ tech }}</a>
      {% endfor %}
    </div>
    
    <div class="project-links">
      <button class="btn-coming-soon" disabled>Coming Soon</button>
    </div>
  </div>
  {% endfor %}
</div>

---

{% if site.author.github %}Want to see the code? Some projects are available on [GitHub](https://github.com/{{ site.author.github }}).{% endif %}

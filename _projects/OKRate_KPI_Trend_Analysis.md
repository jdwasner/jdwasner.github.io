---
layout: project
title: OK Rate KPI Trend Analysis
date: 2024-05-01
description: Developed a suite of dashboards focused on OK Rate (yield) performance across entire production line and individual equipment
featured: True
featured_order: 6
skills:
  - Business Intelligence (BI)
  - SQL
  - KPI
  - Data Visualization
  - Stakeholder Collaboration
---

## Overview

Developed a suite of dashboards focused on OK Rate (yield) performance across entire production line and individual equipment. Designed multiple KPIs to reflect different operational perspectives, enabling leadership and engineers to understand yield trends and focus improvement

## Problem

Prior to this project, OK Rate (yield) visibility was fragmented and inconsistent. Different teams used different calculation methods, leading to confusion and misalignment during performance reviews. Leadership lacked a unified view of yield trends across the production line, and engineers struggled to identify which equipment or processes were driving yield losses.

Key challenges included:
- No standardized definition of OK Rate across departments
- Yield data existed in the datalake but required manual queries to access
- Leadership reviews relied on ad-hoc reports with inconsistent time periods and calculation logic
- Equipment-level yield trends were difficult to compare side-by-side
- No clear mechanism to distinguish between systemic yield issues vs. random variation

Without a centralized, standardized view, improvement efforts were reactive and lacked clear prioritization based on data.

## Solution

I designed and built a comprehensive suite of yield-focused dashboards that provided multiple perspectives on OK Rate performance:

**Calculation Standardization:**
- Worked with stakeholders to define multiple KPIs that reflected different operational needs (e.g., raw yield, normalized yield, first-pass yield)
- Ensured all calculations were transparent, documented, and aligned with business logic

**Dashboard Suite:**
- **Line-Level Dashboard**: Visualized overall production line yield trends over time with drill-down by shift, day, and week
- **Equipment-Level Dashboard**: Enabled side-by-side comparison of individual equipment yield performance with statistical control limits
- **Pareto Analysis**: Highlighted top yield loss contributors by equipment, process step, and product type
- **Trend Analysis**: Provided moving averages and variance tracking to distinguish signal from noise

**Technical Implementation:**
- Built SQL queries to pull and aggregate raw production and inspection data from the datalake
- Designed visualizations that aligned with engineering and leadership decision-making workflows
- Automated refresh schedules to ensure dashboards reflected current performance

The dashboards were integrated into the existing BI platform, providing a single source of truth for yield performance across the organization.

## Impact

Became a primary tool for process engineering leadership to monitor yield performance and prioritize equipment-level investigations. Enabled data-driven focus on process improvement activities.

## Gallery

*Coming Soon!*

## Code Repository

Due to proprietary production data, source code is not publicly available.
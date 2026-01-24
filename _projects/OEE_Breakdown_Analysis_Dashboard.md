---
layout: project
title: OEE Breakdown Analysis Dashboard
date: 2025-05-01
description: Designed and delivered an OEE breakdown dashboard that transformed existing equipment and downtime data into a clear, actionable view of top contributors to equipment losses
featured: True
featured_order: 7
skills:
  - Business Intelligence (BI)
  - SQL
  - KPI
  - Data Visualization
  - Stakeholder Collaboration
  - Dashboard
  - DataLake
  - Trend Analysis
  - OEE
---

## Overview

This project delivered an OEE (Overall Equipment Effectiveness) breakdown dashboard that transformed raw equipment and downtime data into a clear, actionable view of top loss contributors. The dashboard provided process engineering and maintenance leadership with visibility into availability, performance, and quality losses at the equipment level, enabling data-driven prioritization of improvement activities.

## Problem

Equipment performance data existed in the datalake, but there was no centralized view that broke down OEE into its core components (Availability, Performance, Quality) at the equipment level. Engineers and managers faced several challenges:
- OEE losses were tracked, but root causes and top contributors were unclear
- Investigations into equipment performance required manual SQL queries and spreadsheet analysis
- Different teams used inconsistent methods to calculate and interpret OEE metrics
- Leadership lacked a unified tool to identify which equipment and loss types required immediate attention

Without a systematic breakdown of losses, improvement efforts were reactive and often focused on the wrong targets, leading to inefficient use of engineering resources.

## Solution

I designed and built an SQL-backed dashboard that:
- Connected to the production datalake to retrieve equipment runtime, downtime events, throughput, and quality data
- Calculated OEE and decomposed it into Availability Loss, Performance Loss, and Quality Loss for each piece of equipment
- Visualized top loss contributors using Pareto charts, trend lines, and equipment-level breakdowns
- Enabled filtering by time period, process area, and equipment group for flexible analysis
- Provided drill-down capability to investigate specific downtime events or performance deviations

The dashboard was built within the existing BI framework and refreshed automatically, ensuring leadership always had access to current, reliable performance metrics.

## Impact

Became a primary tool for process engineering and maintenance leadership to monitor yield performance and prioritize equipment-level investigations. Enabled data-driven focus on process improvement activities.

## Gallery

*Coming Soon!*

## Code Repository

Due to proprietary production data, source code is not publicly available.
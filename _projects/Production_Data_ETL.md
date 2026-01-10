---
layout: project
title: Production Data ETL & Reporting Pipeline
date: 2023-01-20
description: Built a daily Python ETL pipeline that queried a web API for raw production data, performed complex conditional counting and summarization, and stored the data for downstream visualization in Power BI.
featured: false
featured_order:
featured_image:
skills:
  - Pandas
  - Matplotlib
  - SQL
  - Feature Engineering
  - Python
  - Requests
  - ETL
  - Data Aggregation
  - Power BI
  - DAX
  - Power Query
  - CSV
  - Paraquet
---

## Overview

This project focused on automating the ingestion, transformation, and delivery of daily production data to support reliable reporting and operational decision-making. Prior to this work, key production metrics were generated manually, resulting in delays, inconsistent results, and limited visibility for downstream users.

The goal of the project was to create a repeatable, automated pipeline that produced a trusted, analysis-ready dataset each day and fed directly into reporting tools used by engineering, quality, and manufacturing teams.

## Problem

Production data was available through a web API, but accessing and preparing it for reporting required manual effort each day. This created several issues:
- Daily metrics required manual data pulls and spreadsheet-based processing  
- Report creation was time-consuming and prone to inconsistency  
- Stakeholders lacked timely access to up-to-date production performance  
- Analysts spent more time preparing data than analyzing it  

As reporting demand increased, the existing approach did not scale.

## Solution

I built an automated ETL pipeline in Python to reliably collect, process, and store daily production data for downstream reporting.

Key components of the solution included:
- Querying a production data API using Python  
- Parsing, cleaning, and validating raw records  
- Performing conditional counting and aggregation logic to compute key metrics  
- Storing transformed datasets in analysis-ready formats for Power BI consumption  
- Scheduling the pipeline to run daily and refresh reporting automatically  

The pipeline was designed to be robust, readable, and easy to maintain as reporting needs evolved.

## Impact

- Automated ingestion and preparation of 50k+ production records per day  
- Reduced daily metric report creation time from ~1 hour to ~5 minutes  
- Enabled multiple teams to access up-to-date production metrics each morning  
- Improved consistency and trust in reported metrics by standardizing transformations  

## Gallery

*Coming Soon!*

## Code Repository

Due to proprietary production systems and data, source code is not publicly available.  
This project is documented to demonstrate ETL design, automation logic, and reporting impact.


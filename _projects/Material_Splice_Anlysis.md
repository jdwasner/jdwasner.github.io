---
layout: project
title: Material Splice Performance Analysis
date: 2024-11-15
description: Performed a comparative analysis of four continuous film materials to identify which material most strongly affected equipment output
featured: false
featured_order:
featured_image:
skills:
  - Python
  - Pandas
  - Matplotlib
  - SQL
  - Feature Engineering
  - Data Visualization
  - Exploratory Data Analysis (EDA)
---

## Overview

This project focused on determining how the position within continuous material rolls influenced output parameter variation and product NG (non-good) rates. Four continuous materials (cathode, anode, upper separator, and lower separator) were used simultaneously in the process, making it difficult to isolate which inputs most strongly affected quality.

Rather than treating materials as static inputs, this analysis aligned each produced unit with its **relative position within each material roll** (beginning, middle, or end) to better understand how material transitions and roll behavior contributed to variation and defects.

## Problem

Production quality issues were increasing, but root cause was unclear because multiple continuous materials were changing simultaneously. Traditional comparisons failed to capture how **where a unit was produced within a material roll** influenced downstream quality.

Key challenges included:
- Four continuous materials affecting the process at the same time  
- Material transitions occurring continuously during production  
- Lack of visibility into how roll position impacted output variation  
- Difficulty prioritizing which material stream to investigate during NG events  

Without accounting for material position, investigations risked misidentifying variability and pursuing ineffective corrective actions.

## Solution

I built an analytical framework that aligned production output with material roll position and quantified its relationship to NG rate.

The approach included:
- Querying production and material tracking data using SQL  
- Aligning each output unit with its relative position in the roll (beginning, middle, end) for all four materials  
- Assigning a positional score to each material stream, with middle-of-roll representing the ideal condition  
- Aggregating and comparing combined material position scores against observed NG rates  
- Visualizing relationships between roll position, variation, and quality outcomes

This scoring-based approach allowed material effects to be compared consistently, even when multiple materials changed concurrently.

## Impact

- Identified which material roll positions most strongly correlated with increased NG rates (Cathode and Anode)
- Enabled engineering teams to prioritize investigation and corrective actions on the highest-risk material conditions  
- Improved root-cause clarity during material transition-related quality events  
- Established a repeatable framework for analyzing continuous material effects on quality  

## Gallery

*Coming Soon!

## Code Repository

Due to proprietary production data, source code is not publicly available.
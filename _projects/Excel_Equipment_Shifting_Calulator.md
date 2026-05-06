---
layout: project
title: Excel Equipment Shifting Calculator
date: 2024-11-15
description: Built an Excel tool that translated machine adjustments into expected measurement changes, using historical data to guide faster and more accurate corrections.
featured: true
featured_order: 2
featured_image: /assets/images/Excel Equip Calc Image 004.png
skills:
  - Power Query
  - Excel
  - Complex Excel Functions
---

## Overview

I built an Excel-based decision tool to help engineers and technicians make equipment alignment adjustments with confidence. The tool used Power Query to automatically pull recent historical measurement data, then translated proposed machine moves into expected downstream changes.

In simple terms: instead of guessing which knob to move and by how much, users could test adjustments in the calculator first and see the predicted outcome before touching the machine.

This calculator gets its data from the [Production Data ETL](/projects/production-data-etl/) project, which uses Python to pull and process production data every 24 hours.

## Problem

Before this tool, equipment adjustments were slow and error-prone:

- Different stations used different coordinate systems (same physical move, different direction labels)
- Teams had to manually translate moves between stations
- Small translation mistakes led to extra downtime and repeated trial-and-error

Even experienced engineers could misinterpret direction changes across stations, especially during urgent troubleshooting.

## Solution

I designed a guided Excel calculator that combined coordinate translation logic with auto-loaded historical data.

The model mapped three coordinate “languages” used across the line:
- **Global (g):** shared reference frame
- **System (r):** station-level machine coordinates (X/Y)
- **Stack (s):** local stack coordinates (a/b)

![Coordinate system overview](/assets/images/Excel Equip Calc Image 001.png)
*Coordinate origin reference used to keep all stations aligned to a common baseline*

I documented how movement transforms at each station so users could move from one coordinate system to another reliably.

![Station transformation mapping](/assets/images/Excel Equip Calc Image 002.png)
*Transformation table showing how direction changes are translated by station*

For example, at **R160 Setdown**, a move in **+Y** (system coordinates) maps to **+a** in stack coordinates.

![Production line segment diagram](/assets/images/Excel Equip Calc Image 003.png)
*Process map for one line segment, used to validate station-to-station transformations*

Users interacted with the tool by entering trial adjustment values in **yellow cells** and reviewing predicted outcomes in **green cells**.

![Calculator input/output view](/assets/images/Excel Equip Calc Image 004.png)
*Input/output section used during adjustment planning*

The goal was to match predicted values (green) to historical offset targets (blue/red rows loaded from ETL data via Power Query), then apply only the needed adjustments on the equipment.

Example: adjusting **R160** and **R205** in the X direction can produce a combined X/Y correction at the downstream vision station, reducing measured offset.

## Impact

This calculator became a weekly troubleshooting tool for both maintenance and engineering teams. It:

- Reduced trial-and-error during routine alignment corrections
- Improved first-pass accuracy by grounding decisions in historical data
- Lowered avoidable downtime caused by coordinate translation mistakes
- Provided a repeatable process that was easier to train and hand off

## Code Repository

Due to proprietary production data, source code is not publicly available.

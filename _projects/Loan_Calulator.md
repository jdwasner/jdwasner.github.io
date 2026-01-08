---
layout: project
title: Python Loan Calculator
date: 2023-12-23
description: A Python tool that simulates loan payoff strategies to identify the fastest and most cost‑efficient path to becoming debt‑free.
featured: true
featured_order: 3
skills:
  - Python
  - Pandas
  - Numpy
github: https://github.com/jdwasner/Loan_Calculator
---
**Role:** Developer

**Skills:**
- Python
	- Pandas
	- Numpy

## Overview
Managing multiple loans with different balances and interest rates made it difficult to determine the most cost‑effective payoff strategy. Manually iterating scenarios in Excel was slow and error‑prone, so I built a Python‑based optimization tool that simulates payoff strategies, compares interest and duration outcomes, and exports results for analysis.

## Problem
Questions like *“Which loan should I pay first?”* or *“How much faster can I finish if I increase my payment?”* required repetitive manual calculations. I needed an automated, scalable way to evaluate strategies and understand trade‑offs.

## Solution
I developed a loan modeling engine that:
- Ingests loan data (balance, rate, minimum payment)
- Iterates through weighted payoff strategies (interest‑priority, cost‑priority, payment‑priority)
- Simulates different monthly payment amounts
- Calculates total interest, total payments, and months to payoff
- Exports amortization tables and comparison results to CSV
This produced a complete payoff landscape showing optimal strategies and diminishing‑return thresholds.

## Impact
- Identified the most cost‑efficient payoff order
- Quantified how increased monthly payments reduce payoff time
- Eliminated hours of manual Excel work
- Created a reusable tool for long‑term financial planning

## Gallery

![Example loan detail input into the code](/assets/images/PythonLoanCalculator_Image01.png)
*Example loan detail input into the code*

<img src="/assets/images/PythonLoanCalculator_Image02.png" alt="Example monthly budget vs months to complete iteration output" class="img-medium">
*Example monthly budget vs months to complete iteration output*

![Example amortization table output (continues to the left and down)](/assets/images/PythonLoanCalculator_Image03.png)
*Example amortization table output (continues to the left and down)*

![Example totals by loan output](/assets/images/PythonLoanCalculator_Image04.png)
*Example totals by loan output*

## Code Repository
Source code available on GitHub:
https://github.com/jdwasner/Loan_Calculator

## Future Improvements
- Add visualizations (interest curves, payoff timelines, strategy comparisons)
- Build a simple UI or web app for non‑technical users
- Package as a CLI tool or Python module
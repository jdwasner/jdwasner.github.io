---
layout: project
title: Python Loan Calculator
date: 2023-12-23
description: Built calculating scripts in python to help determine best loan payoff strategy.
technologies:
  - Python
  - Pandas
  - Numpy
github: https://github.com/jdwasner/Loan_Calculator
demo: ""
---
## Overview
After graduating college and purchasing a vehicle, I found myself managing several loans at once. I suspected there was an optimal payoff strategy that would minimize total interest and reduce the time to become debt‑free — but manually iterating scenarios in Excel was slow and error‑prone.

To solve this, I built a Python‑based loan optimization engine that ingests loan data, simulates payoff strategies, evaluates cost and duration trade‑offs, and exports results for analysis.

*Project completed: December 2023*
## Problem
Managing multiple loans with different balances, interest rates, and minimum payments makes it difficult to answer questions like:
- Which loan should I prioritize first?
- How much faster can I finish if I increase my monthly payment?
- What strategy minimizes total interest paid?
My original workflow involved brute‑force calculations in Excel. I needed a scalable, automated solution.

## Methodology
### 1. Set up Loan Information
Each loan is defined by its current balance, interest rate, and minimum monthly payment.

| Loan ID | Current  | Rate   | Monthly |
| ------- | -------- | ------ | ------- |
| Loan01  | 3793.01  | 0.076  | 85.23   |
| Loan02  | 23407.56 | 0.1124 | 450.52  |
| Loan03  | 5039.98  | 0.07   | 70.14   |
| Loan04  | 4860.71  | 0.042  | 79.93   |
| Loan05  | 5351.44  | 0.048  | 79.5    |
| Loan06  | 14312.28 | 0.0419 | 416.47  |
| Loan07  | 5323.07  | 0.0404 | 57.45   |
| Loan08  | 5536.36  | 0.0351 | 66.33   |
### 2. Weight Distribution Iteration
I tested 21 payoff strategies by varying the weighting between:
- **Interest rate priority** (similar to the avalanche method)
- **Total cost priority**
- **Monthly payment priority**
This created a grid of strategies ranging from “all weight on interest rate” to “all weight on total cost.”

```python
#%% Weight Distribution Iteration
#Make range of weights for rate and total
weight_rate_range = np.arange(0,1.05,0.05).tolist()
weight_rate_range = [round(val, 3) for val in weight_rate_range]
weight_total_range = sorted(weight_rate_range, reverse=True)

#Make weight coordinates (weight_rate, weight_total)
coordinates = list(zip(weight_rate_range, weight_total_range))

#Make empty df to store results
df_iter_table = pd.DataFrame(columns=['rate_weight','weight_total','Intrest_Total','Payments_Total', 'Months'])
df_iter_Priority = pd.DataFrame(columns = range(8))

#Iterate through coordinates
for coord in coordinates:
    print(coord)
    weight_rate = coord[0]
    weight_total = coord[1]
    
    #Pass coords, weight and loan info to fn
    result = Loan_Table(weight_rate, weight_monthly, weight_total, Payment, Loan_Info, Start_Date, End_Date)
    
    #Store fn results
    result_summary = result[0]
    result_table = result[1]
    result_months = result[3]
    intrest_total = result_summary.loc['Intrest','Sum']
    payment_total = result_summary.loc['Payment','Sum']

    new_row = {'rate_weight':weight_rate, 'weight_total':weight_total, 'Intrest_Total': intrest_total, 'Payments_Total':payment_total, 'Months':result_months}

    df_iter_table.loc[len(df_iter_table)] = new_row
    df_iter_Priority.loc[len(df_iter_Priority)] = result[2]
```
This allowed me to compare payoff order, total interest, and time to completion across all strategies.
### 3. Payment Range Iteration
Next, I simulated different monthly payment amounts to understand how increased payments affect payoff time and total interest.
```python
#%% Payment Range Iteration

#Make empty df to store results
df_iter_Payment = pd.DataFrame(columns = ['Monthly', 'Intrest_Total', 'Payments_Total', 'Months'])

#Input the best rates from prev iteration
weight_rate = 1.0
weight_monthly = 0.0
weight_total = 0.0

for i in Payment_Range:
    
    print(i)
    
    result = Loan_Table(weight_rate, weight_monthly, weight_total, i, Loan_Info, Start_Date, End_Date)
    
    result_summary = result[0]
    result_table = result[1]
    result_months = result[3]
    
    intrest_total = result_summary.loc['Intrest','Sum']
    payment_total = result_summary.loc['Payment','Sum']
    
    new_row = {'Monthly':i,'Intrest_Total': intrest_total, 'Payments_Total':payment_total, 'Months':result_months}
    
    df_iter_Payment.loc[len(df_iter_Payment)] = new_row
```
This produced a full payoff curve showing diminishing returns as payments increased.
### 4. Save Results
All results — amortization tables, strategy comparisons, and payment simulations — are exported to CSV for easy review.
```python
#%% Save Results
# Create Export folder if it doesn't exist
export_folder = os.path.join(path, 'Export')
os.makedirs(export_folder, exist_ok=True)

df_iter_Payment.to_csv(os.path.join(export_folder, 'Monthly vs Total Cost.csv'))
df_iter_Priority.to_csv(os.path.join(export_folder, 'Loan Order Iterations.csv'))

best_table = Loan_Table(weight_rate, weight_monthly, weight_total, 2000, Loan_Info, Start_Date, End_Date)

best_table[1].to_csv(os.path.join(export_folder, 'Amortization Table.csv'))
best_table[0].to_csv(os.path.join(export_folder, 'Summary.csv'))
df_iter_table.to_csv(os.path.join(export_folder, 'Weight Iterations.csv'))
```
## Impact
This project gave me:
- A data‑driven payoff strategy tailored to my loans
- A clear understanding of how monthly payment changes affect payoff time
- A reusable tool for future financial planning
It also eliminated hours of manual Excel work and replaced it with a scalable, automated solution.
## Technologies Used
- **Python**
- **Pandas & NumPy**
- **Spyder IDE**
- **Git & GitHub**
## Code Repository
Source code available on GitHub:
https://github.com/jdwasner/Loan_Calculator
## Future Improvements
- Add visualizations (interest curves, payoff timelines, strategy comparisons)
- Build a simple UI or web app for non‑technical users
- Package as a CLI tool or Python module

## Conclusion
This project strengthened my Python skills, especially around data manipulation, iteration, and financial modeling. More importantly, it provided real financial value by helping me choose the optimal path to becoming debt‑free.

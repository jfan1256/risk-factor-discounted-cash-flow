# dcf
Discounted Cash Flow

## Introduction
DCF, in short, applies a discounted rate (a temporal rate that accounts for rate of return in the future) to projected future cash flows. By applying the discount rate, the analysis effectively discounts the future values back to the present value, arriving at the terminal value. Lastly, the sum of the terminal values leads to the enterprise value, which can be adjusted accordingly to the firm. This equity value gets compared to the current market value to determine undervaluation or overvaluation. This code allows you to easily calculate the WACC rate for any company. 

## WACC
Initialize the github repo on your local computer and setup a venv/conda environment. Run the notebook and update the fundamental data on the last couples of lines and you will get your WACC rate. 

## Example
In this notebook Emerson Eletric Co. (EMR) WACC was calculated. The steps are as followed:

#### Calculating the Cost of Equity (COE). The traditional method to calculate COE is using the CAPM model on a yearly interval: 
Risk-Free Rate of Return + Beta × (Market Rate of Return – Risk-Free Rate of Return)
To improve on the limitations of CAPM, a more robust model (higher R^2 than CAPM) was utilized to predict on a monthly interval. The model incorporates ETF returns (retrieved from yahoo finance), macroeconomic data (retrieved from SEC), and Fama-French (retrieved from Kenneth French): 

Risk-Free Rate of Return + (ETF Beta + Fama Beta + Macro Beta) × (Market Rate of 
Return – Risk-Free Rate of Return)

The combined predictors totaled to 25 different beta coefficients (the beta in the table below equals the mean of these 25 coefficients). Since EMR’s returns were regressed/predicted on a monthly basis, annual returns were calculated by compounding each year's monthly returns respectively. The timeframe for regression was ‘2018-01’ to ‘2023-06’. For further information and access to the code follow this github repo I made.

#### Calculating the Cost of Debt (COD). The COD was calculated using the following formula: Interest Expense / Total Book Value of Debt. 

#### Plugging into WACC formula:
WACC = (Cost of Equity * % Equity) + (Cost of Debt * % Debt)(1-Tax Rate) + 
(Preferred Shares * % Preferred Shares)

% Equity, % Debt, and Tax Rate were calculated from EMR’s Q3 2023 CFS, IC, and BS documents. The calculated WACC was 4.7%. 


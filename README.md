
# **Systematic 13F Hedge Fund Alpha Replication Project**
**Author: Shengwei Huang**

## **Project Overview**
This project replicates key findings from research papers focused on generating alpha by analyzing **13F filings of hedge funds**. The goal is to explore whether public information from institutional holdings can be used to construct a profitable trading strategy.

In this replication, we construct a portfolio based on the top hedge fund stock picks, focusing on **conviction** and **consensus**. We test multiple strategies, including the best performing **Top 40 stocks with a 10% conviction threshold**, and backtest the portfolio using daily stock returns.

## **Key Features**
1. **Data Extraction**:
   - Collected **13F filings** data from the SEC to analyze institutional holdings.
   - Used **Python web scraping** techniques to gather and clean data.

2. **Strategy Design**:
   - Selected stocks based on hedge fund **conviction** (position size in the portfolio) and **consensus** (number of funds holding the stock).
   - Applied a **47-day delay** in portfolio construction to account for the 13F reporting lag.
   - Tested strategies based on conviction thresholds (e.g., 0.05, 0.075, 0.1).

3. **Backtesting**:
   - Implemented a backtesting framework to evaluate the portfolio’s performance.
   - Calculated metrics such as **cumulative return**, **annualized return**, **volatility**, **Sharpe ratio**, **tracking error**, and **information ratio**.
   - Visualized the **monthly returns** using a heatmap.
   - Conducted **risk analysis** using **Value at Risk (VaR)** and **Conditional Value at Risk (CVaR)** with historical, parametric, and Monte Carlo methods.

4. **Risk Parity Portfolio Experiment**:
   - Implemented a **Risk Parity** approach, distributing risk equally across the top 40 high-conviction stocks.
   - Evaluated the performance compared to equal-weighted portfolios.

## **Results**
- **Best Strategy**: 
  - **Top 40 Stocks, 10% Conviction Threshold**:
    - **Cumulative Return**: **515.41%**
    - **Annualized Return**: **15.81%**
## Performance Comparison

This plot shows the performance comparison of different portfolios:
- **13F Portfolio Equal Weight**
- **13F Portfolio Risk Parity**
- **S&P 500**
- **S&P 500 Equal Weight**

![image](https://github.com/user-attachments/assets/908d60b3-44c0-4665-bcea-33f1e0398456)

## Monthly Returns Heatmap

This heatmap visualizes the monthly returns over time, showcasing the volatility and performance of the portfolio on a monthly basis.

![image](https://github.com/user-attachments/assets/a90fcc06-7c93-4978-b417-a8efcd04f8aa)

### Key Insights:

- **Best Year**: **2019** with an average return of **2.85%**, driven by strong returns in **January (10.83%)** and **June (6.53%)**.
- **Worst Years**: **2018 (-0.44%)** and **2022 (-1.92%)** were marked by significant losses, especially in **December 2018 (-10.32%)** and **December 2022 (-7.08%)**.
- **Best Month**: **June** consistently delivered the highest returns across multiple years, with an average of **4.03%**.
- **Worst Month**: **December** shows the most volatility, with negative averages due to large drawdowns in 2018 and 2022.
- **Volatility**: **2020** had extreme swings with **March (-13.80%)** followed by a strong recovery in **June (14.24%)** and **November (11.16%)**.
- **2023** shows positive performance so far, especially in **January (9.96%)** and **June (7.62%)**.

### Summary:
The portfolio performs best in **June** and **January**. **December** tends to be the most volatile month, with significant losses in bad years. While 2019 and 2017 had strong, steady gains, **2020** saw sharp volatility due to the pandemic.


## Performance Statistics

The table below summarizes the key performance statistics for each portfolio strategy:

![image](https://github.com/user-attachments/assets/bc96b4a4-ac88-4688-aaef-b4a7c6ac01ec)

### Performance Statistics Analysis

- **13F EW** (15.81% return, 19.05% volatility) delivers the highest **annual return** and **best risk-adjusted performance** (Sharpe ratio of 0.78), indicating that high-conviction stock picks from institutional investors outperform the market, despite higher volatility.

- **13F RP** (13.39% return, 18.67% volatility) offers **lower risk** than 13F EW, but its **Sharpe ratio of 0.66** shows slightly less efficient risk-adjusted returns. However, its lower **tracking error** (4.46%) demonstrates better consistency compared to the benchmark.

- **S&P 500** (11.30% return, 17.18% volatility) and **S&P 500 EW** (11.27% return, 17.81% volatility) provide more stable returns, but with lower **Sharpe ratios** (0.60 and 0.58), indicating less efficient use of risk.

- **Annual Outperformance**: 13F EW outperforms the S&P 500 by 4.51%, while 13F RP still adds 2.10% outperformance annually.

- **Information Ratio**: 13F EW (63.98%) and 13F RP (47.05%) far exceed S&P 500 EW, showing significantly higher excess returns relative to risk.

### Summary:
The **13F EW portfolio** achieves the best risk-adjusted performance despite higher volatility. **13F RP** offers a more balanced risk profile with slightly lower returns but better risk management. Traditional indices, while more stable, lag behind in terms of both return and risk efficiency.



## Fama-French 6-Factor Analysis

The table below shows the results of an OLS regression analysis using the **Fama-French 6 factors** to explain the portfolio's excess returns on a monthly basis. The 6 factors include **Market Risk Premium (Mkt-RF)**, **Small Minus Big (SMB)**, **High Minus Low (HML)**, **Robust Minus Weak (RMW)**, **Conservative Minus Aggressive (CMA)**, and **Momentum (MOM)**.

### Fama-French 6-Factor Analysis

The table below shows the results of an OLS regression analysis using the **Fama-French 6 factors** to explain the portfolio's excess returns on a monthly basis. The 6 factors include **Market Risk Premium (Mkt-RF)**, **Small Minus Big (SMB)**, **High Minus Low (HML)**, **Robust Minus Weak (RMW)**, **Conservative Minus Aggressive (CMA)**, and **Momentum (MOM)**.

```plaintext
                            OLS Regression Results                            
==============================================================================
Dep. Variable:          Excess Return   R-squared:                       0.917
Model:                            OLS   Adj. R-squared:                  0.913
Method:                 Least Squares   F-statistic:                     232.9
Date:                Tue, 10 Sep 2024   Prob (F-statistic):           5.13e-66
Time:                        11:08:10   Log-Likelihood:                -228.78
No. Observations:                 134   AIC:                             471.6
Df Residuals:                     127   BIC:                             491.8
Df Model:                           6                                         
Covariance Type:            nonrobust                                         
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
const          0.1773      0.125      1.421      0.158      -0.070       0.424
Mkt-RF         1.0136      0.031     32.774      0.000       0.952       1.075
SMB           -0.1352      0.056     -2.422      0.017      -0.246      -0.025
HML            0.0868      0.050      1.720      0.088      -0.013       0.187
RMW           -0.1122      0.068     -1.653      0.101      -0.247       0.022
CMA           -0.0949      0.075     -1.270      0.206      -0.243       0.053
MOM           -0.0148      0.037     -0.396      0.693      -0.089       0.059
==============================================================================
Omnibus:                       16.057   Durbin-Watson:                   1.927
Prob(Omnibus):                  0.000   Jarque-Bera (JB):               21.148
Skew:                           0.679   Prob(JB):                     2.56e-05
Kurtosis:                       4.394   Cond. No.                         5.50
==============================================================================

Notes:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.

```
## Risk Analysis: Distribution of Weekly Portfolio Returns

This section provides an in-depth **risk analysis** of the weekly returns for the portfolio, focusing on the 95% **Value at Risk (VaR)**. VaR is a widely-used risk management tool that estimates the potential loss in the value of a portfolio over a defined period for a given confidence interval (in this case, 95%).

### Kolmogorov-Smirnov Test Results

The Kolmogorov-Smirnov (K-S) test compares the empirical cumulative distribution function (CDF) of the observed data with theoretical distributions (Normal, T-distribution, and Gamma) to assess the goodness of fit. The K-S statistic represents the maximum distance between the empirical CDF and the theoretical CDF, with a smaller K-S statistic indicating a closer fit. Here are the results:

| Distribution     | K-S Statistic | P-value |
|------------------|---------------|---------|
| **Normal**       | 0.0690        | 0.0071  |
| **T-Distribution**| 0.0255        | 0.8295  |
| **Gamma**        | 0.0784        | 0.0014  |

#### Interpretation:
- **T-Distribution**: With a K-S statistic of **0.0255** and a high p-value of **0.8295**, the T-distribution provides the closest fit to the observed data. The large p-value indicates that we fail to reject the null hypothesis, meaning that the T-distribution is a good fit.
- **Normal Distribution**: The K-S statistic is **0.0690** with a p-value of **0.0071**. While the Normal distribution is reasonably close, the low p-value suggests that it does not fit the data as well as the T-distribution.
- **Gamma Distribution**: The K-S statistic is **0.0784** and the p-value is **0.0014**, indicating a significant deviation between the observed data and the Gamma distribution.

Based on the K-S test, the **T-distribution** is the best fit for the observed returns data.

#### K-S Test Plot:
The following plot shows the empirical CDF compared with the theoretical CDFs of the Normal, T-distribution, and Gamma distributions. The dashed vertical lines represent the K-S statistic, highlighting the maximum difference between the empirical and theoretical CDFs.


![image](https://github.com/user-attachments/assets/bb595483-3bcf-4d96-b35c-2c9a159389a6)


### AIC and BIC Analysis

The Akaike Information Criterion (AIC) and Bayesian Information Criterion (BIC) are used to assess the goodness of fit of statistical models while penalizing for model complexity. Lower AIC and BIC values indicate a better fit, with a balance between goodness of fit and simplicity.

#### AIC and BIC Values:
The AIC and BIC values for the Normal, T-distribution, and Gamma distributions are as follows:

| Distribution     | AIC       | BIC       |
|------------------|-----------|-----------|
| **Normal**       | 2720.78   | 2729.53   |
| **T-Distribution**| 2617.57   | 2630.69   |
| **Gamma**        | 2735.43   | 2748.56   |

#### Interpretation:
- The **T-Distribution** has the lowest AIC (**2617.57**) and BIC (**2630.69**) values, suggesting it provides the best balance between model fit and complexity among the tested distributions.
- The **Normal** and **Gamma** distributions have higher AIC and BIC values, indicating they do not fit the data as well as the T-distribution.

#### AIC and BIC Plot:
The plot below shows the AIC and BIC values for the different distributions, visually highlighting the superiority of the T-distribution.

![image](https://github.com/user-attachments/assets/3fa84946-b0ff-4287-9909-6347a3b73994)




### Value at Risk (VaR) Methods:
We have calculated VaR using four different methods, each providing a slightly different approach to estimating the risk:
1. **Parametric VaR (Normal Distribution)**: Assumes returns follow a normal distribution. It is one of the most commonly used methods but may underestimate risk in the presence of heavy tails.
2. **Parametric VaR (T-Distribution)**: Uses the T-distribution, which accounts for fatter tails and can better capture extreme events.
3. **Historical VaR**: Directly uses historical returns to calculate VaR, without making any assumptions about the distribution of returns.
4. **Monte Carlo Simulation (T-Distribution)**: Simulates potential future returns based on a fitted T-distribution to estimate VaR. This method allows for flexibility in modeling complex scenarios.

### VaR Plot:

The following plot visualizes the distribution of weekly portfolio returns, with **Royal Blue** representing the distribution and kernel density estimate (KDE) curve, while the **Steel Blue** dashed lines highlight the VaR values for each method.

![image](https://github.com/user-attachments/assets/8e08d1b0-001f-417d-8554-aba30d887cee)

#### Key Observations:
- **Parametric Normal VaR**: -3.72%  
  Assumes normally distributed returns and is prone to underestimating tail risk, particularly during periods of financial turbulence.
  
- **Parametric T-distribution VaR**: -5.03%  
  This method accounts for fatter tails, providing a more conservative estimate of risk than the normal distribution.

- **Historical VaR**: -3.38%  
  Based on actual historical data, this provides a more empirical estimate of risk, although it may be biased by unusual events in the past.

- **Monte Carlo Simulation VaR (T-distribution)**: -3.27%  
  Uses simulated returns based on the T-distribution, offering a flexible and robust estimate of potential risk.

#### Risk Implications:
- **Higher VaR values** (as seen with the T-distribution) suggest a higher risk of extreme losses, which can be crucial for portfolios exposed to volatile or non-normally distributed assets.
- **Monte Carlo Simulation** and **T-distribution-based VaR** capture tail risk more effectively, which is vital in volatile market conditions.

## Conclusion

This research successfully replicated and extended the findings of previous studies on hedge fund alpha generation using publicly available **13F filings**. By constructing portfolios based on institutional investors' high-conviction stock picks and incorporating a systematic, data-driven approach, this project demonstrates that information from **13F filings** can be leveraged to build profitable trading strategies.

The core methodology involved selecting stocks based on **conviction**—the percentage weight of a stock within a fund's portfolio—and **consensus**—the number of funds holding a particular stock. This study evaluated multiple thresholds and strategies, such as **Top 40 Stocks with a 10% Conviction Threshold**, providing empirical evidence for the potential of this approach to generate superior risk-adjusted returns compared to traditional benchmarks.

### Key Findings:

1. **Performance Superiority of 13F-Based Portfolios**:  
   The **13F Equal-Weighted (EW) portfolio** achieved an **annualized return of 15.81%**, significantly outperforming the **S&P 500 (11.30%)** and **S&P 500 Equal-Weight (11.27%)** over the same period. Additionally, the **13F Risk-Parity (RP) portfolio** produced a **13.39% annualized return**, reflecting its potential as a balanced alternative, with a more stable risk-return tradeoff. This performance confirms that institutional investors' high-conviction positions can be a reliable source of excess returns for systematic investors.

2. **Conviction and Consensus as Alpha Drivers**:  
   The results reaffirm the hypothesis that conviction and consensus among institutional investors play a critical role in identifying alpha-generating stocks. Stocks with higher conviction exhibited stronger performance, while filtering based on consensus helped improve the selection process by ensuring that selected stocks were backed by multiple funds. This highlights the importance of incorporating both conviction and consensus into portfolio construction when utilizing **13F filings** for investment strategies.

3. **Risk Management Insights**:  
   The analysis of **Value at Risk (VaR)** and **Conditional Value at Risk (CVaR)** through historical, parametric, and Monte Carlo methods provides robust insights into the risk characteristics of the 13F portfolios. The **T-distribution-based VaR** and **Monte Carlo simulations** were particularly effective in capturing tail risk, emphasizing the need for advanced risk models in portfolios that contain high-conviction, concentrated positions. Traditional **Normal VaR** models, while useful, were found to underestimate risk, especially during periods of high market volatility.

4. **Statistical Validation of Distribution Fit**:  
   The **Kolmogorov-Smirnov test** and **AIC/BIC analysis** confirmed that the **T-distribution** offers the best fit for the portfolio returns, effectively capturing the heavier tails and extreme events in the data. This reinforces the argument that models assuming normality are insufficient for risk management in portfolios with exposure to extreme market movements, and that distribution-based approaches must be tailored to reflect the realities of financial market dynamics.


In conclusion, this research demonstrates that systematically extracting insights from institutional investors through **13F filings** can lead to superior portfolio performance. By combining conviction-based stock selection with advanced risk management techniques, investors can achieve robust returns while adequately accounting for potential risks. As markets evolve and data availability improves, the integration of these approaches will likely become an increasingly critical component of successful investment strategies.


## References

1. Angelini, L., Iqbal, M., & Jivraj, F. (2019). *Systematic 13F Hedge Fund Alpha*. First version: October, 2019.

2. Palomar, D. P. *Risk Parity Portfolio*.


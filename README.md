# R&D Portfolio Testing 

### Introduction
Companies with R&D expenditures may outperform the market as they are thought to be on the forefront of innovation. Secondly, because R&D expenses may suppress reported earnings in the short term, companies with this expense may be undervalued. By examining both value-weighted and equally weighted portfolios, this analysis seeks to explore if alphas exist for portfolios constructed with companies that invest in research and development (R&D). Through this approach, the project will explore if investing in companies with this expenditure is a viable strategy for investors seeking superior performance to the return of the market.

### Data
Wharton WRDS was used to access the datasets necessary for this research. Annual fundamental data, including R&D expense and revenue per company was downloaded using Compustat. For returns data, CRSP monthly returns (version 2) was used with important variables including monthly price (MthPrc), monthly market capitalization (MthCap) and monthly returns (MthRet). Additionally, the Ken French data library was used to download monthly risk-free rates, as well as the market returns minus the risk free rate. For this analysis, we used January 1980 – December 2022.

### Pre-processing
For this analysis, several pre-processing steps were necessary to clean and wrangle the data into a useable format.
To merge annual fundamentals data with monthly returns, the CRSP-Compustat linking table was used, with linktypes of LC, LU, and LS. 
Here is a short list of the additional steps that were taken:   
  
•	Only used exchanges 11-19  
•	Only used companies listed as USA  
•	Excluded financial and pharmaceutical companies   
•	Removed MthRet values less than 100  
•	Converted MthRet units by multiplying by 100  
•	Lagged market cap by one month  
•	Lagged fundamentals by 1 year to avoid look ahead bias   
•	R&D expense: If NA, then convert to 0. If revenue is missing as well, then the row was removed. The assumption that if financial data was missing then, a N/A for R&D expense may not indicate 0.  

### Exploratory Data Analysis
Firstly, I explored what percent of firms made an R&D expense in a given year. It appears there has been a steady upwards trajectory towards more companies spending on R&D.  


<div align="center">
  <img src="https://github.com/user-attachments/assets/a0ecd709-52d5-4e87-8b3c-54ee95acab8b" alt="Image 1 description">
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/a5bf793c-96ac-408b-ba4a-c581e7692784" alt="Image 2 description">
</div>

I found it interesting that R&D expense appears to spike in 2021. This appears to align with the hefty spending that firms did following the COVID-19 pandemic.
Lastly, I evaluated if there was any noticeable in historical returns for firms with & without R&D expense.  

<div align="center">
  <img src="https://github.com/user-attachments/assets/06e1b492-cb8f-4fc3-bcd1-c4611f83ff36" alt="Centered Image">
</div>

### Portfolio Construction
Equally-weighted portfolio
Equally weighted portfolios do not consider the size of each stock’s contribution to the overall market, therefor each stock is equally weighted within the portfolio. The returns of this portfolio is simply the equal weight multiplied by excess return. 
Value-weighted portfolio
Firstly, market capitalization for each stock in each time period was calculated by multiplying the price of the stock by the shares outstanding. Next, total market capitalization for each time period was calculated by summing the market capitalization for all stocks at each time period, for with and without R&D expense. To arrive at a total portfolio, all value weighted returns were then summed for companies with R&D expense, and without at each month.

### Results
Univariate linear regressions were performed on the excess returns of the market using each of the portfolios created.  

<div align="center">
  <img src="https://github.com/user-attachments/assets/a131eceb-336f-4e84-8a3b-310657e055c4" height="300" width="800" alt="Centered Image">
</div>

The beta values are close to 1, reflecting that the assets in the portfolios move nearly in tandem with the market. All alpha values are low and statistically insignificant, indicating that there are no excess returns beyond what would be anticipated from market exposure. High R-squared values suggest that the models explain a significant portion of the variance in portfolio returns.

### Conclusions
This analysis found no statistically significant evident to suggest that portfolios of firms with R&D expenses produce excess returns (alpha) compared to the market. Both value-weighted and equally-weighted portfolios exhibited similar results, with beta values close to 1 and insignificant alphas. While R&D expenditure is important for innovation and companies’ long-term growth, the results suggest that it does not necessarily translate into superior short-term portfolio performance relative to the market.




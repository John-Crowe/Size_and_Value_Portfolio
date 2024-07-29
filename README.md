# Size and Value Portfolio

In this project, we are concerned with replicating the ME-sorted deciles (Market Equity), BM-sorted deciles (Book to Market), High Minus Low (HML) and Small Minus Big (SMB) factors. These portfolios are described in depth in French and Fama's 1992 paper "The Cross-Section of Expected Stock Returns" and their 1993 paper "Common Risk Factors in the Returns on Stocks and Bonds". This replication uses CRSP Raw, CRSP Delisted, CRSP CSTAT data and CRSP Datalink, and CRSP Pension data. We need all of these dataframes to download stock data and the corresponding accounting data. 

The risk free rate is from the French Fama numbers (not CRSP) which we download below, per the directions. We will combine the 'dlret' and 'ret' columns for the stocks and redefine 'ret' to encompass all returns for these stocks. We will filter our stocks to only use the 10 and 11 sharecodes and the 1, 2 and 3 exchanges, per the French Fama website. Both the ME and BE portfolios are divided based on the NYSE stocks, meaning each decile has an equal amount of NYSE stocks. We do this so the large cap stocks (which tend to be in the NYSE) do not generally favor one specific decile. This is especially important for the ME decile replicaiton. Our returns are shown as excess returns.

We use all non financial firms in the intersection of (a) the NYSE, AMEX, and NASDAQ return files from the Center for Research in Security Prices (CRSP) and (b) the merged COMPUSTAT annual industrial files of income-statement and balance-sheet data, also maintained by CRSP. Furthermore, we exclude financial firms because the high leverage that is normal for these firms probably does not have the same meaning as for nonfinancial firms, where high leverage more likely indicates distress. These are all requirements from the French Fama papers.

To ensure that the accounting variables are known before the returns they are used to explain, we match the accounting data for all fiscal year ends in calendar year with the returns for July of year $t$ to June of year $t+1$. The 6-month (minimum) gap between fiscal year end and the return tests is conservative and used to ensure that this information would be available at the time of portfolio replication at the end of June each year.

We use a firm's market equity at the end of December of year $t-1$ to compute its book-to-market, leverage, and earnings-price ratios for year $t-1$, and we use its market equity for June of year t to measure its size. Thus, to be included in the return tests for July of year $t$, a firm must have a CRSP stock price for December of year $t-1$ and June of year t. 

The final output is between January 1973 and December 2023.

# Relevant Libraries
* wrds
* pandas
* pandas-datareader
* numpy
* scipy
* matplotlib

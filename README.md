# Building Factor Portfolios for Indian Market using Machine Learning
# Factor Portfolios have been around for quite some time. Globally Asset Managers have been moving from taking bets on stocks to bets on Factors. Below are couple of Factors which have been quite popular:
## 1. Momentum Factor: Return of a stock over 12m - 1m. This Factor counts on taking bets on stocks having good historical returns.

## 2. Value Factor: There are couple of definitons for this factors relying on taking bets on stocks with high earnings/price, book value/ price, EBIT/ Enterprise Value

## 3. Quality Factor: Again there are multiple definitons here where we suggest to take bets on stocks with high ROE and low leverage(Debt/Equity) ratios

## 4. Dividend: This factor signifies taking bet on stocks with high divident yield(Div/Price)

## 5. Growth Factor: This factor has multiple variants again taking bet on stocks with fast earning, sales, opeerating cash flows.

## 6. Machine Learning based Multi Factors: A Machine Learning based Factor Portoflio can be created in mutiple ways as below:

# 1. Given a holding period of say 1 month I wish to attain a cumulative threshold return like 2%, 5%, 7.5%.

# 2. Given a holding period of say 1 month I wish to minimize the Standard Deviation of return.

# 3. Given a holding period of say 1 month I wish to attain Risk Adjusted Return(Sharpe Ratio) threshold like 0.8, 1.2, 1.5.

# While there are a lot of materials available to build such portfolios for US Markets. There are very few for Indian markets. I attempt here to leverage proven Quant methodlogies to test Factors in Indian market. 

## I use a lot of Open Source Materials for building/testing Single/ Multi-Factor Portfolios. Here I use Yahoo for Market Price Data. Screener.in for Fundamental Data testing Factors on Nifty 500 universe which is a broad index to track Large, Mid& Small cap companies.

# Below are Steps to run all Jupyter notebooks in order.

## Step 1: Run Step1_Extract_Yahoo_Data_Nifty500.ipynb to extract all Pricing Data for NIFTY500 stocks for Yahoo Finance.

## Step 2: Run Step2_Extract_Screener_Data_Nifty500.ipynb to extract all Fundamental Data for NIFTY 500 companies from Screener.in website. Here we use Selenium and Beautiful Soup for all Data Extraction.

## Step 3: Run Step3_Integrate_Fundamental_Market_Data_nifty500.ipynb for extracting all Fundamental and Market data for downstream bakctesting and Alpha Lens Evaluation.

## Step 4: Build a Machine Learning Factor with predicted value of objective(Return, Risk, Sharpe Ratio) being used as a Factor. We are using Light GBM model for classification here(If Objective > threshold return then 1 else 0). We use all the popular individual factors as features for the model like Momentum, Value, Growth, Dividend Yield, Quality. Below are also details of the steps:
##    a. Define the objective you want to attain over holding period like return(2%,5%,7.5%).
##    b. Define a Supervised Learning Problem where we class objective as 1 if actual value is greater than objective else 0.
##    c. Create Train Test Data with 80%,20% split and Hyper Parameter Tuning for best model selection.
##    d. Plot Factor Importance and check model soundness with precison, recall & F-scores.
##    e. Use the model to predict over entire data set and this factor becomes a Multi Factor ML Model.
##    f. Dump the data from further downstream backtesting and Alpha Factor evaluation.

## Step 5: Step4_Backtesting_Stocks_nifty500.ipynb for building and bakctesting long only factors over various recon dates. Here we use BT & FFN libraries.

## Step 6: Step5_Run_ Factor_Alpha_Lens.ipynb for testing Significace of Long Short Alpha, Information Coefficient, Factor Auto Co-rrelation etc.

## All output(Backtesting Metric, Alpha Lens Output, Plots) gets geenrated in data folder.

# Below are some caveats:

## 1. This is a research project and should not be used for investment decission making. 

## 2. I am using lot of Open Source Data so there may be some data quality issues. 

## 3. I am using latest NIFTY Holdings(2020). Hence there will be survivorship bias in the data during backtesting exercise.

## 4. All analysis is ex-Transaction Cost.
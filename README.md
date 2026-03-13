 Trader Behavior Insights Using Market Sentiment
 
 Project Overview

This project analyzes the relationship between cryptocurrency market sentiment and trader performance.

Using the Bitcoin Fear & Greed Index and historical trading data from Hyperliquid, the goal is to uncover patterns in how traders behave during different market emotions.

Market sentiment often influences decision-making in financial markets. Understanding how traders perform during Fear, Greed, and Neutral periods can help build smarter trading strategies.

 Objective

The objective of this analysis is to:

Explore the relationship between market sentiment and trader profitability

Identify patterns in trading behavior

Understand how trade size and sentiment influence profits

Discover insights that can improve algorithmic or manual trading strategies

 Dataset Description
1️ Fear & Greed Index Dataset

This dataset represents the market sentiment of the cryptocurrency market.

Columns:

Column	Description
timestamp	Unix timestamp
value	Fear & Greed score
classification	Market sentiment (Fear, Greed, Neutral)
date	Calendar date

Example:

Date	Sentiment
2018-02-01	Fear
2018-02-14	Greed
2️ Hyperliquid Trader Dataset

This dataset contains historical trading activity.

Columns include:

Column	Description
Account	Trader wallet address
Coin	Asset traded
Execution Price	Price where trade executed
Size Token	Number of tokens traded
Size USD	Value of trade in USD
Side	Buy / Sell
Timestamp	Time of trade
Start Position	Position before trade
Direction	Trade direction
Closed PnL	Profit or Loss
Fee	Transaction fee
Trade ID	Unique trade identifier
⚙️ Data Processing Pipeline
Step 1 — Data Loading

Datasets were loaded using Python Pandas.

trades = pd.read_csv("historical_data.csv")
sentiment = pd.read_csv("fear_greed_index.csv")
Step 2 — Data Cleaning

Data preprocessing steps included:

Removing missing values

Converting timestamps

Formatting column names

Handling numeric conversions

Example:

trades['timestamp'] = pd.to_datetime(trades['timestamp'], unit='ms')
sentiment['date'] = pd.to_datetime(sentiment['date'])
Step 3 — Feature Engineering

A date column was extracted from trade timestamps to align with the sentiment dataset.

trades['date'] = trades['timestamp'].dt.date
Step 4 — Data Integration

The datasets were merged to associate each trade with the market sentiment on that day.

merged = pd.merge(trades, sentiment[['date','classification']], on='date', how='left')
📊 Exploratory Data Analysis

The following analyses were performed:

Profit Distribution

Understanding how profits vary across sentiment categories.

Trade Size Analysis

Analyzing how trade sizes vary during different market conditions.

Trader Behavior

Examining whether traders prefer buying during fear or selling during greed.

Daily Profit Trends

Tracking profit trends across time and sentiment.

 Visualizations
1️ Profit Distribution by Sentiment

This visualization shows how profits and losses vary across sentiment conditions.

Generated file:

pnl_distribution_by_sentiment.png

Insight:
Greed markets tend to show more consistent profits, while fear markets show higher volatility.

2️ Daily Trader Profit Trend
daily_pnl_by_sentiment.png

Shows how trader profits change over time depending on market sentiment.

3️ Trade Size Distribution
trade_size_distribution.png

Reveals how frequently traders execute large trades.

 Key Insights
1️ Market Sentiment Influences Profitability

Average trader profitability tends to increase during Greed sentiment periods.

Greed markets usually indicate strong bullish momentum, which traders exploit.

2️ Fear Markets Show Higher Loss Volatility

During Fear sentiment, trader losses increase significantly due to panic selling and high uncertainty.

3️ Trade Size Increases During Bullish Sentiment

The analysis shows that large trades occur more frequently during Greed markets, suggesting stronger trader confidence.

4️ Profit Distribution is Highly Skewed

A small percentage of traders generate most profits, while the majority experience smaller gains or losses.

This follows a power-law distribution, common in financial trading ecosystems.

5️ Trader Behavior is Momentum Driven

Many traders appear to follow momentum-based strategies, buying during rising markets rather than contrarian trading.

 Strategic Recommendations

Based on the findings:

Recommendation 1

Implement risk controls during Fear markets to reduce downside volatility.

Recommendation 2

Use sentiment indicators as a feature in algorithmic trading models.

Recommendation 3

Monitor trade size spikes as a signal of market confidence.

 Tools & Technologies Used

Python

Pandas

Matplotlib

Seaborn

Jupyter Notebook

Git

GitHub

 Project Structure
Trader-Behavior-Insights
│
├── analysis.ipynb
├── historical_data.csv
├── fear_greed_index.csv
├── merged_data.csv
│
├── daily_pnl_by_sentiment.png
├── pnl_distribution_by_sentiment.png
├── trade_size_distribution.png
│
└── README.md

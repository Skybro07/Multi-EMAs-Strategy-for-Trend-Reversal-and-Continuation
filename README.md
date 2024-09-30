# Multi-EMAs-Strategy-for-Trend-Reversal-and-Continuation
"Multi-EMAs Strategy for Trend Reversal and Continuation"

-	Hypothesis
-	Examples
-	Stock selection and target
-	Implementation
-	sample run
-	Visualizing the results
-	Conclusion
-	suggestions


Hypothesis:
My strategy is based on the hypothesis that the simultaneous use of multiple exponential moving averages (EMAs) of varying periods along with the closing and opening price of the stocks can effectively identify potential trend reversals and continuations in financial markets. The hypothesis assumes that when these EMAs are in a specific configuration (either in the uptrend or downtrend), they can provide insights into the underlying market sentiment and price momentum.

EMAs period used: 20,25,30,35,40,45,50,55

The strategy seeks two key scenarios:

Scenario 1:

When all the EMAs are in an uptrend i.e. EMA20>EMA25>EMA30>EMA35>EMA40>EMA45>EMA50>EMA55 enter in the long trade
when the close price of the candle is above the EMA20 and open is below EMA55.

Scenario 2:

When all the EMAs are in a downtrend i.e. EMA20<EMA25<EMA30<EMA35<EMA40<EMA45<EMA50<EMA55 enter in the long trade
when the close price of the candle is above the EMA55 and open is below EMA20.

The strategy also incorporates volume on the entry candle should be greater than the average of the past 10 candles' volume


Example of how trade initiates:

•	First check if all the EMAs are either in ascending or descending order.
•	Considering in the ascending order, if the current closing price is above the 20-period EMA.
•	Check for the opening price below the 20-period EMA.
 
•	If these conditions are satisfied then check for the volume to ensure that the current volume is greater than the 10-period SMA of volume.
•	If all conditions are met, a buy order is placed.

Few examples based on the different timeframes:




AXIS BANK hourly timeframe chart and a significant move of 8.42% after the buy signal candle(Trend continuation)


 
PFC hourly time frame chart and a significant move of 17% after the buy signal candle ( Trend reversal)



Axis bank hourly chart and a significant bullish move after the entry signal candle (Trend reversal)


 

PFC 30 minutes time frame and a significant move of the 6% after the entry candle


TATA POWER 15-minute time frame chart and an 8.98% upside move after the entry signal candle (Trend reversal)


So, after seeing the strategy robustness in the different timeframes, I am using an hourly timeframe chart for backtesting the strategy This strategy works on any timeframe chart without any exception just need to change the target and stop loss depending on the timeframe.


Target and stop loss
The strategy uses a stop loss set at 5% below the buy price and a target sell price set at 5% above the buy price.
More sophisticated approaches could also involve the concept of trailing stop loss


Stock selection criteria:
This strategy works with its full potential on highly liquid stocks actively traded on the exchange. So, selecting some of the most liquid stocks on the NSE based on market cap
1.	AXIS Bank (Large cap)
 
2.	ITC
3.	ICICI Bank
4.	Power finance corporation (PFC)
5.	WIPRO
Implementation of the strategy:
Coding the strategy in python using the backtrader library CODE- Code


Data source- using the trading view as the data source, after downloading the data from the trading view data is stored in a CSV (Comma-Separated Values) file format.
Using the pd.read_csv for reading the data
Backtesting period:
Backtesting the strategy from 1st January 2020 till the present
The sample period underwent economic events like COVID-19, the Russia-Ukraine Conflict, and the 2020 Farmer Protest. the sample period has also gone through country-specific and global geopolitical events.


Some assumptions during the backtest:
•	Slippage is negligible.
•	My strategy first checks if there's an existing order; if there is, it does not execute any new orders.
•	I am not taking leverage in trades as some of the trades take more than a day, so considering Indian market trades aren’t eligible for leverage
Result format:
•	Result shows the date when buy executed and sell executed including CMP at that time
•	Shows the number of trades closed, number of win trades, number of losing trades, number of open trades, and strike rate (Win ratio).


Conducting a sample run of the strategy on JINDALSTEEL over a one-year lookback period to gain a better understanding of the result format.
 
 
 
 

 
Visualizing the results for the bucket of stocks:
Here is the backtesting result of each stock from 1st January 2020:




After combining the overall result for 5 stocks:



Conclusion:
•	This trading strategy showcases a systematic approach to capturing potential trends and reversals in financial markets, relying on the power of EMAs, price analysis, and volume confirmation.
•	This strategy has great potential not only in the Indian financial markets But also works with no limitation in the other global markets as it is purely based on the opening and closing data.
•	A high degree of market liquidity is essential for the strategy to be successful.
Recommendations:
•	This is only a long strategy one can convert this into a long short strategy
•	The concept of the trailing stop loss can be used to maximize the profit

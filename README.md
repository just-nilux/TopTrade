# TopTrade

TopTrade is a machine leaning system that aims to predict whether a certain cryptocurrency is a buy or a sell over a specified trading period. For the purpose of this project, the cryptocurrencies that I will be focusing on are Bitcoin, Ethereum, Litecoin and Bitcoin Cash because they are among the most prominent cryptocurrencies. This project includes data wrangling, data visalization, feature engineering, preprocessing data, generating models and hyperparameter tuning. The following document will outline the high level approaches I have taken to develop this project. 

## Introduction
### Data
The data in this project was sourced from the Poloniex API. The Poloniex API gives access to data from the most popular cryptocurrencies, including the ones that I will be using, at a variety of granularities. For each of the four cryptocurrencies we are interested in the close and the volume values at the minute level. The close is the cryptocurrencies market price at the end of the minute interval and the volume is the amount of units that were exchanged during the minute interval. Below is initial structure of the data as described above: 

<img width="672" alt="Screen Shot 2020-01-07 at 10 10 23 PM" src="https://user-images.githubusercontent.com/34798787/71947517-1f1e6900-319b-11ea-960d-d607dd76753b.png">

### Features 
With the goal of flexibilty in mind, I would like the ability to dynamically change the cryptocurrency that will predicted. This means that the preliminary set of features that the underlying model will use to generate the predictions will consist of the historical values of the volume of the cryptocurrency being predicted along with the historical values of the volume and close of the remaining three cryptocurrencies. It is my hope that this set of features will offer insight into the price movement of the target cryptocurrency. The high level hypothesis I am making is that the prices and volumes of cryptocurrencies are related in some way. In order to test this assumption, I looked into how the prices of the various cryptocurrencies are correlated. This was done by taking the original dataset and selecting only columns corresponding to cryptocurrencies prices (4 in total). I then normalized this data by taking the percentage change between subsequent values in each columns. The pearson correlation coefficitents were then calculated between the cryptocurrencies. An illustrustion of the aforementioned analysis is below: 

<img width="368" alt="Screen Shot 2020-01-07 at 5 40 13 PM" src="https://user-images.githubusercontent.com/34798787/71948527-47f42d80-319e-11ea-82f5-9a3725bb2551.png">

As evidenced by the values of the pearson correlation coeficients exceeding .5, there is some degree of relationship between the price movement of the various cryptocurrencies. This relationship can potentially be exploited by a model to predict whether a cryptocurrency is a buy or a sell over a specified trading period. 

### Feature Engineering
Based on our existing features, I will derive additional potentially insightful features. This process is known as feature engineering. In particular, I will be creating features based on the price movement of the target cryptocurrency referred to as technical indicators. Technical indicators are a mathematical calculation based on historic price, or other related information, that aims to forecast the direction of the price of an asset. Below is a list of technical indicators that were derived: 

- **7 Interval Moving Average:** The average of the prices over the last 7 intervals.
- **21 Interval Moving Average:** The average of the prices over the last 21 intervals.
- **12 Interval Exponential Moving Average:** The average of the prices over the last 12 intervals with more wighting to more recent prices. 
- **26 Interval Exponential Moving Average:** The average of the prices over the last 26 intervals with more weighting to more recent prices. 
- **20 Interval Standard Deviation:** The standard deviation of the 20 previous intervals. 
**Bollinger Bands:** A Bollinger Band® is a technical analysis tool defined by a set of lines plotted two standard deviations (positively and negatively) away from a simple moving average (SMA) of the price

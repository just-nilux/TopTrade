# TopTrade

## Introduction 
TopTrade is a machine leaning system that aims to predict whether a certain cryptocurrency is a buy or a sell over a specified trading period. For the purpose of this project, the cryptocurrencies that I will be focusing on are Bitcoin, Ethereum, Litecoin and Bitcoin Cash because they are among the most prominent cryptocurrencies. This project includes data wrangling, data visalization, feature engineering, preprocessing data, generating models and hyperparameter tuning. The following document will outline the high level approaches I have taken to develop this project. 

## Data 
The data in this project was sourced from the Poloniex API. The Poloniex API gives access to data from the most popular cryptocurrencies, including the ones that I will be using, at a variety of granularities. For each of the four cryptocurrencies we are interested in the close and the volume values at the minute level. The close is the cryptocurrencies market price at the end of the minute interval and the volume is the amount of units that were exchanged during the minute interval. Below is initial structure of the data as described above: 
<img width="672" alt="Screen Shot 2020-01-07 at 10 10 23 PM" src="https://user-images.githubusercontent.com/34798787/71947517-1f1e6900-319b-11ea-960d-d607dd76753b.png">

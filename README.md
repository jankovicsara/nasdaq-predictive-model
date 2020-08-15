# Nasdaq Predictive Model

### V0.1.0

![NASDAQ Image](/Images/Nasdaq-copy.jpg)

## Purpose and Goal of this Project/Repository

As markets become increaseingly more volatile, and trading becomes more automated thanks to algorythmic trading, it has become more significant to take in a larger volume of information to make better informed decisions regarding investments in markets around the globe - more information than can be reasonably expected of a person to parse through and analyze individually. The goal of this project is to create a model that will analyze data fed into it by creating a model based off of historical data and using it to predict returns on future data based on trends. 

This predictive random forest model will focus on NASDAQ companies, and will use data from every single ticker in the exchange over the course of a year from July 2019 to  July 2020 to train amd test the data - over 900,000 data points. Our primary goal is to identify stocks that can be expected to outperform the NASDAQ, and our seconday goal with this is to practice more in the creation of models for forecasting purposes, as well as to familiarize ourselves more with AWS infrastructure, given that we will be using Sagemaker to collaborate on the project. 

### Team 

- Javier Mendez
- Reuben Lopez
- Scott Andersen 
- Sara Jankovic

### Tools Used

- Excel
- Python
- Pandas (Python Library)
- AWS Sagemaker

## Process of Creating the Model 

As all models do (as we have found out), it all begins with finding quality data that can be used to test and train it. We were able to find historical data for every NASDAQ ticker (for a small fee!). We have uploaded a year of this data to this repository so that it can be used by anyone wishing to test the model for themselves - the code is already written to intepret it right away. 

After the data was found, we cleaned it in such a fashion so that we were working with only a "returns" column for every ticker on every day from July 2019 to July 2020. We chose this data for two reasons: 
  
  1. This is *a lot* of data already for a model to train on. over 900,000 individual percentages for this model to learn on. We figured this was more than enough to create something that was accurate enough for our liking. 
  2. The data includes moments:
    A) Before COVID
    B) During the COVID Crash
    C) During the COVID Recovery
   This allows the model to learn from different types of "moments" in the stock market (stability, reduction, and growth).

From here on out, we were able to create the model, which suprisingly enough, often-times can be the easy part (compared to data-aggregation). This was all done on AWS Sagemaker, a service provided by Amazon that allows you to work on Jupyter Notebooks on their servers. This provides access to their massive amounts of processing power which is useful for working on a model with this much data, as well as allows us to more easily collaborate on the code. Here is an example of what some of the code looks like: 

![Code Example](/Images/code-example.gif)

Once we had the model created and running at a level that we liked it, we then go through the process of turning the model wihch is currently split up into multiple Jupyter Notebook cells into a variety of functions, each being a key aspect of the model. This is done so that we are able to connect it to SNS, the Amazon service we are going to be using to send the tickers via email to any users who wish to subscribe to the service the model provides. To get an idea of what this looks like, here is a chunk of the code in cells compared to what it looks like in a function:

![Code Example 2](/Images/transformation.PNG)

With SNS, we can then add emails that wish to recieve the data and the messages with the tickers can be sent whenever the code is run (as of V0.1.0)

## How it works & Application

The model will do the analysis to create a 1-day forecast. With all the data points we fed into it, it "learned" ways to identify ticker movements and we can ask for it to return us the tickers that it believes will move in a positive direction the following day, and will return us the highest movers. 

## Results
The results of the accuracy of the model are below:
![Model Accuracy](/Images/model-accuracy.png)

Additionally, here is an example of what the email subscribers receive:

![Email](/Images/email.png)

## How this is useful for you

There are a variety of ways you can trade with this knowledge, the two most common being:
 1. Momentum Trading (short-term)
 2. Options Trading (Momentum, short-term or long-term).

## Resources

[Useful Article on Random Forest's and how they work.](https://en.wikipedia.org/wiki/Random_forest)

[Data Cleaning Tips and Tricks in Python](https://towardsdatascience.com/data-cleaning-in-python-the-ultimate-guide-2020-c63b88bf0a0d?gi=dd7bd10c80c6)

[AWS Sagemaker Tutorial](https://www.youtube.com/watch?v=8Vj7OaR4DcA)

[Random Forest Regression Article](https://towardsdatascience.com/random-forest-and-its-implementation-71824ced454)

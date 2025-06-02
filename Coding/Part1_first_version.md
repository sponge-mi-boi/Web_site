# The Quant Testing Framework I use to create profitable strategies
Here is my setup for creating profitable strategies in quant. The framework is quite large and still expanding, meaning that I will post each of its aspects individually, and explain how they all fit together. 

The most important classes I'm using are 
- Yggdrasil: the root of all my code
- StockAnalyzer: the state of the strategy being executed on a given stock universe
- StrategyHelper: the state of the strategy itself, separate from a stock universe it can act on
To support these, which are all in different modules for clarity and which I will explain in detail in a later post, are the following modules
- market_analy: contains the raw details of the data upon which I am doing this analysis  
- useful_shi: this is a module of helper functions which helps display code and various results easier and helps in analysis

Below, I post the following module and explain in detail. 
- Module: yggdrasil.py  #Contains the class Yggdrasil
    - class: Yggdrasil  #This is the root of all my strategies and analysis. Creates a general instance of a test.
      - Instance variables: 
        - stock_universe     #List of stocks which will be used in the given test
        - cur_strat          #StrategyHelper object which sets and executes the basic framework of the given strategy in this test 
        - stock_attr_ranked  #Dataframe of all the attributes of the stocks in the universe used in this test ranked compartively. 
        - stock_attr         #Dataframe of all the attributes, or at least the basic ones, of the universe of stocks used in this test.
        - strat              #String representing the strategy being used in this test
        - title              #Defines the various aspects of the strategy being used. 
      - Instance methods:
        - create_helper           #Creates the given StrategyHelper object
          - Required parameters:
            - None
          - Named parameters:
            - stock_list = full_stocks 
            - roll = 25
            - cutoff = 15/10
          - Return: None
        - get_stock_attr          #Creates the given Dataframe of stock attributes 
          - Required parameters:
            - None
          - Named parameters:
            - details = False
        - get_stock_attr_ranked   #Creates the given Dataframe of stock attributes ranked in this universe of stocks 
          - Required parameters:
            - None
          - Named parameters:
            - details = False
    - free code: Saves the results of various parameters to a JSON file 
The results of the free code being run on a sample of a few commonly traded stocks and a mean reversion strategy with a few different parameters are shown below


```python
import time,json,logging
import sys,sqlite3,keyboard
import pandas as pd
import numpy as np
from matplotlib.backends.backend_pdf import PdfPages

from market_analy import full_stocks
from strategy_analy import strategy_analysis, StockAnalyzer
from useful_shi import break_pt, divider, space, format_, format_output, get_attributes, get_method_info
from strategy_helper import StrategyHelper

class Yggdrasil:
    def __init__(self,freq,strategy,custom,shift=0,num_points=500):

        self.stock_universe = []
        self.cur_strat = StrategyHelper(freq,strategy,custom=custom,shift=shift,num_points=num_points)
        
        
        self.stock_attr = None
        self.stock_attr_ranked = None

        self.strat = None
        self.title = ''


    def create_helper(self,stock_list = full_stocks,roll = 25, cutoff = 15/10):
        list_profits = []
        for stock in stock_list:
            self.cur_strat.run_method([stock],roll,cutoff)
            results = [self.cur_strat.results[x] for x in ['Profit','Number of Completed Trades']]  
            if results[0] > 0 and results[1] > 30: list_profits.append([stock] + results)   #Condition used to decide the stock universe is the requirement that the profit of an individual 
        list_profits.sort(key=lambda x:x[1],reverse=True)                                    #trade of that stock is positive and the number of completed trades is at least 30
        self.stock_universe = list_profits
        self.strat = StockAnalyzer(stock_list,self.cur_strat)
        title = ('(freq: ' + self.cur_strat.freq + ', ' + 'num of data points: ' + str(self.cur_strat.num_points) +
                 ', custom: ' + str(self.cur_strat.custom) + ', shift: ' + str(self.cur_strat.shift)
                 + ', start date: ' + str(self.cur_strat.start) + ', end date: ' + str(self.cur_strat.end)
                 + ', roll:' + str(roll) + ', cutoff:' + str(cutoff) + ')' )
        self.title = title
        
    def get_stock_attr(self,details=False):
        self.stock_attr = self.strat.get_aspects_by_stock()
        if details:
            format_(x=self.title, y=self.stock_attr)

    def get_stock_attr_ranked(self,details=False):
        self.strat.get_aspects()
        self.stock_attr_ranked = self.strat.data_ranked
        if details:
            format_(x=self.title,y=self.stock_attr_ranked)
            
example_analysis = []

for shift in range(1):
    ygg = Yggdrasil('5m', 'Mean Rev', True, shift=shift, num_points=100)
    for roll in range(10, 11):
        for cutoff in range(11, 12):
            ygg.create_helper(full_stocks, roll, cutoff / 10)
            example_analysis.append((ygg.title, ygg.stock_universe))

with open('stuff_type_shi.json', 'w') as pdf:
    json.dump(example_analysis, pdf, indent=2)


```

[
  [
    "(freq: 5m, num of data points: 100, custom: True, shift: 0, start date: 2025-05-01 10:20:00-04:00, end date: 2025-05-02 15:55:00-04:00, roll:10, cutoff:1.1)",
    [
      [
        "LLY",
        203.46734619140625,
        31.0
      ],
      [
        "DXCM",
        137.06988525390625,
        31.0
      ],
      [
        "EA",
        42.30247497558594,
        31.0
      ],
      [
        "DOV",
        36.53550720214844,
        33.0
      ],
      [
        "STX",
        33.98908233642578,
        35.0
      ],
      [
        "CTSH",
        24.71501922607422,
        33.0
      ],
      [
        "CVX",
        20.253463745117188,
        33.0
      ],
      [
        "DHI",
        17.290512084960938,
        32.0
      ],
      [
        "SYY",
        6.992362976074219,
        31.0
      ],
      [
        "FE",
        6.1699981689453125,
        35.0
      ],
      [
        "MDLZ",
        4.291816711425781,
        31.0
      ],
      [
        "XEL",
        4.262214660644531,
        32.0
      ],
      [
        "ADM",
        4.070995330810547,
        31.0
      ],
      [
        "K",
        2.8069992065429688,
        31.0
      ],
      [
        "PPL",
        2.5849952697753906,
        36.0
      ],
      [
        "T",
        1.7716999053955078,
        33.0
      ]
    ]
  ]
]

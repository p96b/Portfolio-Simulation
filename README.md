# Trading Platform Simulation
## Overview
Group Project - Simulation of a trading platform: In this simulation, the user can trade stocks of US-listed (NASDAQ, NYSE etc.) companies and cryptocurrencies while using real-life prices. The program has many different functions which all revolve around the trading experience.

The user starts with a self-defined amount of money, which can be used to buy a variety of different stocks or cryptocurrencies. During market hours, the prices shown are real-time, which enables a true trading experience with virtual money. Yet, unlike in real-life, the user can also make trades outside of market hours.

Once invested in a few companies, the user can track his stocks’ performance and sell at the right time to make profits, which are added to his cash account. The program also supports short selling when the user wants to bet on falling prices. 

The user can keep track of his portfolio development over time, as an entry of the portfolio’s value is made every day, which allows the user to analyze his performance over days, weeks, or as long as required. Should the user not open the portfolio for some days, the portfolio value development over these days is still calculated retrospectively and can be analyzed once the user decides to log back into his account. For this purpose, different tables and charts are at the user’s disposal.

Furthermore, the user can add cash to his account at any time, should funds run low at some point. In the same way, it is also possible to reset the portfolio and start anew with an empty portfolio. If there should be any question with regards to some of the program’s functions, it also contains a help section of the most important tools. Reading this section is recommended before starting to trade.
## Project description
The code for this trading platform simulation tool was written by Niklas Wellmanns (20-602-587), Christopher Siegrist (18-618-819), Juliette Kuich (19-615-913), Lukas Stiefel (18-619-478) and Prisca Beutler (16-657-330) for the group project in the course "Skills: Programming - Introduction Level" respectively "Skills: Programming with Advanced Computer Languages" supervised by Dr. Mario Silic at the University of St.Gallen (HSG).  

The coding was done using the Python programming language and uses a variety of libraries and modules, such as the [Pandas Library](https://pandas.pydata.org/), the [Yahoo! Finance market data downloader](https://pypi.org/project/yfinance/), [matplotlib](https://matplotlib.org/) or the [pickle module](https://docs.python.org/3/library/pickle.html).

Most information of this program is stored in pandas dataframes, which are subsequently exported into CSV files to enable the saving of key data after exiting the program and being able to continue at a later stage with the same information. The available cash amount is stored in a pickle file (cash.pk) and updated every time the user completes a buy or sell function.

The code was written and tested for functionality in Jupyter Notebook. We strongly recommend using Jupyter Notebook, but limited testing was also performed using Google Colab and Thonny. Execution using repl.it was rather cumbersome.
## Starting the application
To start the application please download the Code File (“Stock_Simulation.ipynb” for Jupyter Notebook and Google Colab users and “Stock_Simulation.py” for other IDE), and the two CSV files (“Tickers.csv” and “Portfoliovalues.csv”) and save them in the same folder.

For the sake of testing all available functions of our program, we provided a pre-existing portfolio. Certain functions, such as the historical performance line chart only make sense if the portfolio was held for some time (i.e., there are already data points available). In simple terms, we want to avoid that that the program must be used for several days in order to see all available functions. However, the portfolio can be reset at any time using the function in the main menu if you want to start form zero. This function wipes the CSV files and deletes the cash.pk file, which will then be re-created once the user starts the code again. 

Depending on your IDE you might need to install [Pandas Library](https://pandas.pydata.org/), [matplotlib](https://matplotlib.org/), and the [pickle module](https://docs.python.org/3/library/pickle.html) (most of them should be readily installed and only need to be imported). 

Before you can run the code in an IDE such as Jupyter Notebook you first need to install the following plug-ins:
-	[Yahoo! Finance market data downloader](https://pypi.org/project/yahoo-fin/)
-	[Yahoo Finance API](https://pypi.org/project/yfinance/) 
-	[Requests-HTML](https://docs.python-requests.org/projects/requests-html/en/latest/)

These plug-ins should be easily installable using your CMD or terminal function. 
For help, try this [link](https://phoenixnap.com/kb/install-pip-windows).

For Jupyter Notebook and Google Colab, running the following code should install the missing plug-ins:

!pip install yfinance

!pip install yahoo_fin
## Features
The program starts with the main menu which gives the user a complete overview of currency, date, market status, portfolio value, available cash and the programming functions which are explained in more detail in the following. From every point of the program, the user is always able to return to the main menu.<br><br>

In the price finder the user enters a ticker and the program searches on the yahoo_fin module for the live price of this stock and prints it. This is possible for any US listed company or cryptocurrency. <br><br>

In the buy function the user can buy shares of publicly listed companies or cryptocurrencies as long as he has enough available cash. After entering a valid ticker, the current price of the company will be displayed and the user can insert the dollar value he wants to invest. Within the buy function it is also possible to do a short selling (sell stocks that are not held by the user) if there is speculation of falling prices. The user can short sell by entering a negative dollar value during the buying process. Furthermore, the buy function shows the available cash as well as the current portfolio with its performance. It updates according to the CSV file or updates the CSV file after a purchase respectively. <br><br>

With the sell function the user can sell shares which he holds in his portfolio. The user needs to enter the ticker of the stock he wants to sell. The program searches the portfolio for every position held of that ticker and displays these filtered positions in a separate table. This is necessary in case the user holds multiple positions in one company, but only wants to sell one specific one. Therefore, in the next step, the user is asked which position of all those held of the company he typed in previously belonging to the chosen company should be sold. The index of this second table presents the order numbers, which are the same as in the unfiltered portfolio.

By typing the order position, the user is then guided towards the choice of selling the entire position, or only a part of it. If the latter is chosen, he will be asked to specify the exact amount in dollars to sell. This will then be deducted accordingly from the portfolio, while the invested value and the profit/loss will be adjusted proportionally to the amount sold. After the execution of a selling order, the gain or loss of this respective position is displayed to the user. The dataframe is then stored in the CSV file.

After typing in the desired order number, it is possible to sell the whole position at once or just a part of it. Depending on the type of the position (long or short), the user must sell (in a long position) or repurchase (in a short position) shares in order to close the trade and reap a profit (or incur a loss). It is not possible to repurchase shares in long position as this would be equivalent to another buy order, which needs to be executed in the specific buying menu. Equivalently, it is not possible to sell shares in a short position as this would represent another short sale process, which also should be performed in the buying menu.<br><br>

The section “refresh portfolio” updates the entire portfolio dataframe with the most recent stock prices and stores it right back into the CSV file. The user sees the updated values of his holdings. If the markets are closed it will disclaim that the user is outside of trading hours and the prices will reflect those at previous closing. <br><br>

With the option “view portfolio” the user has several opportunities. He can ask for a table showing his current portfolio performance with non-realized profits and losses or a table showing the historic performance of the whole portfolio since the first day of starting the program. The program makes an entry of the portfolio value every day it is opened. In case the user does not open the program for a specific time period, the portfolio values during these days are entered retrospectively based on the closing price of these days. In the same manner, the portfolio value on weekends (non-trading periods) is based on the closing prices of the previous trading day.

Regarding graphs, there is the possibility to print a line chart to analyze the historic portfolio performance or a pie chart to look at the portfolio allocation. The daily portfolio performance is calculated based on the cumulative value of all positions multiplied by the most recent closing price. For every non-trading day, the closing price of the previous trading day is used. The line chart’s meaningfulness increases with the number of days stored, so during the first few days of trading, the line’s meaning might be limited.<br><br>

The “restart portfolio” function allows the user to delete his current portfolio and reset everything to zero. The portfolio positions, all CSV files and the cash account will be deleted or emptied. After resetting, the user must restart the program. As soon as the program has been restarted the user will be asked to define the desired cash amount with which he wants to start over. <br><br>

The function “add cash” gives the user the opportunity to increase the cash amount which he can use for his investments.<br><br>

There is a function to exit the program so that the user can ‘log-out’ of his account without having to manually interrupt the script.<br><br>

Finally, there is a help section with useful tips related to the price finder, the buy function, the sell function as well as about refreshing, viewing and restarting the portfolio.<br><br>

For further information and explanation have a look at the help section in the program or even at the comments in the code.
## Remarks
As this is a simulation it has some limitations and differences in comparison to trading platforms. Out of several limitations that have to be considered we provide you the following three which all arise from the fact that this is just a simulation. Firstly, the user can not influence the stock prices. Even if there is an illiquid stock with little supply and the user buys many shares, the price will not increase whereas on a real trading platform this could be the case. Secondly, the prices are only updated every time the code is executed so if e.g. the user waits some seconds until he decides to buy/sell a stock it would be possible in this simulation that he decides on the basis of an older price and the buy/sell would be executed on the current price which might be different from the previously displayed one. Thirdly, there might be some differences in the tables where the user gets an overview over his portfolio as we round the quantity and the price and calculate the other values on the basis of the rounded values. Another difference to other trading platforms is that in our simulation it is also possible to buy and sell positions outside of trading hours. In this case the respective closing rates of the previous trading day is used. This makes our simulation more flexible.

To understand the single lines in the code please read through the comments. Should you have any questions, do not hesitate to contact niklas.wellmanns@student.unisg.ch, christopher.siegrist@student.unisg.ch, juliette.kuich@student.unisg.ch, lukas.stiefel@student.unisg.ch or prisca.beutler@student.unisg.ch. 

Disclaimer: The program was completely tested with the latest versions of Jupyter Notebook and briefly tested using Google Colab and Thonny on the 28th of May 2021 CEST. Running the code with other programs, other versions of Python or other machine time may cause errors. Further, the website links and the available data on these websites may change over time. 

This stock simulation is for entertainment purposes only and was designed as part of a university course. It does not constitute any financial advice and the developers do not carry any liability in connection with the program’s use for real financial transactions.

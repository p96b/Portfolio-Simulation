# Trading Platform Simulation
## Project description
Group Project - Simulation of a trading platform: In this simulation, the user can trade stocks of US-listed companies and cryptocurrencies while using real-life prices. The program has many different functions which all revolve around the trading experience.

The user starts with a self-defined amount of money, which can be used to buy a variety of different stocks or cryptocurrencies. During market hours, the prices shown are real-time, which enables a true trading experience with virtual money. Yet, unlike in real-life, the user can also make trades outside of market hours.

Once invested in a few companies, the user can track his stocks’ performance and sell at the right time to make profits, which are added to his cash account. The program also supports short selling when the user wants to bet on falling prices. 

The user can keep track of his portfolio development over time, as an entry of the portfolio’s value is made every day, which allows the user to analyze his performance over days, weeks, or as long as required. Should the user not open the portfolio for some days, the portfolio value development over these days is still calculated retrospectively and can be analyzed once the user decides to log back into his account. For this purpose, different tables and charts are at the user’s disposal.

Furthermore, the user can add cash to his account at any time, should funds run low at some point. In the same way, it is also possible to reset the portfolio and start anew with an empty portfolio. If there should be any question with regards to some of the program’s functions, it also contains a help section of the most important tools. Reading this section is recommended before starting to trade.
## Project description
The code for this trading platform simulation tool was written by Niklas Wellmanns (20-602-587), Christopher Siegrist (18-618-819), Juliette Kuich (19-615-913), Lukas Stiefel (18-619-478) and Prisca Beutler (16-657-330) for the group project in the course "Skills: Programming - Introduction Level" respectively "Skills: Programming with Advanced Computer Languages" supervised by Dr. Mario Silic at the University of St.Gallen (HSG). 

The coding was done using the Python programming language and uses a variety of libraries and modules, such as the [Pandas Library](https://pandas.pydata.org/), the [Yahoo! Finance market data downloader](https://pypi.org/project/yfinance/), [matplotlib](https://matplotlib.org/) and the [pickle module](https://docs.python.org/3/library/pickle.html).

Most information of this program is stored in pandas dataframes, which are subsequently exported into CSV files to enable the saving of key data after exiting the program and being able to continue at a later stage with the same information.

The code was written and tested for functionality in Jupyter Notebook, which was recommended by the Professor during the course’s individual tasks.

We strongly recommend using Jupyter Notebook, but limited testing was also performed using Google Colab and Thonny. Execution using repl.it was rather cumbersome.
## Starting the application
To start the application please download the Code File (“Stock_Simulation.ipynb” for Jupyter Notebook and Google Colab users and “Stock_Simulation.py” for other IDE), the two CSV files (“Tickers.csv” and “Portfoliovalues.csv”), and the pickle file “cash.pk” and save them in the same folder.

For the sake of judging our project, we provided two sets of the above-mentioned files. One set is completely empty and allows the user to start from zero. The other set is prefilled with a portfolio of different stocks. Certain functions, such as the historical performance line chart only make sense if the portfolio was held for some time (i.e., there are already data points available) and we want to pre-empt any constraints that could arise during the evaluation of the project and the Professor’s time. In simple terms, we want to avoid that that the program has to be used for several days in order to see all available functions.

However, the portfolio can be reset at any time using the function in the main menu. This function wipes the CSV files and deletes the cash.pk file, which will then be re-created once the user starts the code again. 

To summarize:
-	Save the Tickers_filled.csv and Portfoliovalues_filled.csv and cash.pk if you want to start with the pre-existing portfolio --> use the reset function in the main menu to start from zero
-	Save the empty Tickers.csv and Portfolio_values.csv (without the cash.pk!) if you want to start from zero directly

Depending on your IDE you might need to install [Pandas Library](https://pandas.pydata.org/), [matplotlib](https://matplotlib.org/), and the [pickle module](https://docs.python.org/3/library/pickle.html) (most of them should be readily installed and only need to be imported). 

Before you can run the code in an IDE such as Jupyter Notebook you first need to install the following plug-ins:
-	Yahoo! Finance market data downloader --> [click here](https://pypi.org/project/yahoo-fin/)
-	[Yahoo Finance API](http://theautomatic.net/yahoo_fin-documentation/) --> [click here](https://pypi.org/project/yfinance/)
-	Requests-HTML --> [click here](https://docs.python-requests.org/projects/requests-html/en/latest/)

These plug-ins should be easily installable using your CMD or terminal function. 
For help, try this link: https://phoenixnap.com/kb/install-pip-windows

## Features
The program starts with the main menu which gives the user a complete overview of currency, date, market status, portfolio value, available cash and the programming functions which are explained in more detail in the following. From every point of the program, the user is always able to return to the main menu.

In the price finder the user enters a ticker and the program searches on the yahoo_fin module for the live price of this stock and prints it. This is possible for any US listed company or cryptocurrency. 

In the buy function the user can buy shares of publicly listed companies or cryptocurrencies as long as he has enough available cash. After entering a valid ticker, the current price of the company will be displayed and the user can insert the dollar value he wants to invest. Within the buy function it is also possible to do a short selling (sell stocks that are not held by the user) if there is speculation of falling prices. The user can do short selling by entering a negative dollar value during the buying process. Furthermore, the buy function shows the available cash as well as the current portfolio with its performance. It updates according to the CSV file or updates the CSV file after a purchase respectively. 

With the sell function the user can sell shares which he holds in his portfolio. It is possible to sell a whole position or just a part. After the execution of a selling order the gain or loss of this respective position is displayed. Furthermore, the sell function updates the portfolio according to the CSV file respectively updates the CSV file after the execution of a selling order.

The section “refresh portfolio” updates the entire portfolio dataframe with the most recent stock prices and stores it right back into the CSV file. The user sees the updated values of his holdings. If the markets are closed it will disclaim that the user is outside of trading hours and the prices will reflect those at closing.

With the option “view portfolio” the user has several opportunities. He can ask for a table showing his current portfolio performance with non-realized profits and losses or a table showing the historic performance of the whole portfolio. Regarding graphs, there is the possibility to print a line chart to analyze the historic portfolio performance or a pie chart to look at the portfolio allocation. The daily portfolio performance is calculated based on the cumulative value of all positions multiplied by the most recent closing price. For every non-trading day the closing price of the previous trading day is used. 

The “restart portfolio” function allows the user to delete his current portfolio and reset everything to zero. The portfolio positions, all CSV files and the cash account will be deleted or emptied. After resetting, the user might have to restart the program. As soon as the program has been restarted the user will be asked to define the desired cash amount with which he wants to start over. 

The function “add cash” gives the user the opportunity to increase the amount which he can use for his investments.

There is a function to exit the program so that the user can ‘log-out’ of his account without having to manually interrupt the script.

Last but not least, there is a help section with useful tips related to the price finder, the buy function, the sell function as well as about refreshing, viewing and restarting the portfolio.

For further information and explanation have a look at the help section in the program or even at the comments in the code.
## Remarks
As this is a simulation it has some limitations and differences in comparison to trading platforms. Out of several limitations that have to be considered we provide you the following three which all arise from the fact that this is just a simulation. Firstly, the user can not influence the stock prices. Even if there is an illiquid stock with little supply and the user buys many shares, the price will not increase whereas on a real trading platform this could be the case. Secondly, the prices are only updated every time the code is executed so if e.g. the user waits some seconds until he decides to buy/sell a stock it would be possible in this simulation that he decides on the basis of an older price and the buy/sell would be executed on the current price which might be different from the previously displayed one. Thirdly, there might be some differences in the tables where the user gets an overview over his portfolio as we round the quantity and the price and calculate the other values on the basis of the rounded values. Another difference to other trading platforms is that in our simulation it is also possible to buy and sell positions outside of trading hours. In this case the respective closing rates of the previous trading day is used. This makes our simulation more flexible.

To understand the single lines in the code please read through the comments. Should you have any questions, do not hesitate to contact niklas.wellmanns@student.unisg.ch, christopher.siegrist@student.unisg.ch, juliette.kuich@student.unisg.ch, lukas.stiefel@student.unisg.ch or prisca.beutler@student.unisg.ch. 

Disclaimer: The program was completely tested with the latest versions of Jupyter Notebook and briefly tested using Google Colab and Thonny on the 28th of May 2021 CEST. Running the code with other programs, other versions of Python or other machine time may cause errors. Further, the website links and the available data on these websites may change over time. 

This stock simulation is for entertainment purposes only and was designed as part of a university course. It does not constitute any financial advice and the developers do not carry any liability in connection with the program’s use for real financial transactions.

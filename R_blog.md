# Data Analytics with R

This document is going to outline how to use R in data analysis. The following is based off of a class I took at New Jerseuy Institute of Technology CsS 636: Data Analytics with R.

## What is R?

R is an interpreted computer language and has has many built-in statistical functions.

Throughout this document we will overview how to use R to import, clean, and modify data used in data analysis.

## Installing R

My prefered way for using R is to interact with it via command line and a jupyter notebook.

With conda `https://conda.io/projects/conda/en/latest/user-guide/install/index.html` You cam create a an r environement like this

```
conda create -n r-environment r-essentials r-base
conda activate r-environment
```

And now R can be run from the command line

```
R

fdsa
```

More often than not you are not going to want ot just just R in you Command Line. A common way to use R is a in a jupyter notebook. I prefer using a classic jupyter notebook.

Install with either pip or conda

```
conda install -c conda-forge notebook

```

OR

```
pip install notebook
```

The by calling `jupyter notebook` you can begin writing and executing your R code in a notebook. More info on using jupyter notebooks can be found here (link)

## Reading data

Lets say we want to view IBM's 2018 stock data. We can load data into out R environment using `read.csv()`.

Download IBM's 2018 data from here: https://finance.yahoo.com/quote/IBM/history?period1=1514782800&period2=1546232400&interval=1d&filter=history&frequency=1d
And save it to your local machine. Then, provide the path to where you save this file as an argument to the function below

```
data <- read.csv("IBM.csv")
```

## Inspecting our data

Lets call the `class()` function on our data so we can learn how to interact with it.

`class(data)` should output the type 'data.frame'.

A dataframe is basically a table or a 2-dimensional array structure that we can use to interact with our data. This aritcle is going to share some common approaches towards interacting with a dataframe in R.

`nrow(data)` reveals that this dataframe as 251 rows. If we print this entire dataframe it is going to take up alot of our screen. Let's use `head()` to print just the first 5 rows.

```
head(data)
```

This allows us to see all of the columns in our table. This is a handy tool to quickly get an idea of what our data might be able to show us. We could also check out the last 5 records using `tail()`.

## Forming our own dataframes

Viewing the IBM stock data can provide us alot of good information, but it might be more interesting to take a look at some other stocks as well.

Let's download 2018 stock data for 9 other companies. Then, we can select which columns we think are important and which columns are irrelevant, and create a new dataframe with all relevant information about our 10 stocks.

Download stock data for MSFT, GOOG, AAPL, AMZN, FB, NFLX, TSLA, ORCL and SAP by replacing IBM's stock ticker in the above the link with these ticker values provided.

Then load each dataframe

```
AAPL = read.csv("data/AAPL.csv")
AMZN = read.csv("data/AMZN.csv")
FB = read.csv("data/FB.csv")
GOOG = read.csv("data/GOOG.csv")
MSFT = read.csv("data/MSFT.csv")
NFLX = read.csv("data/NFLX.csv")
TSLA = read.csv("data/TSLA.csv")
ORCL = read.csv("data/ORCL.csv")
SAP = read.csv("data/SAP.csv")
```

Now we have 10 seperate references to each dataframe - lets combine them in order to make a single dataframe.

### Thoughts to consider

In order to form this new dataframe, we are going to need to consider 2 ideas:

1. Removing unwantned columns
2. Renaming columns so that each column is unique.

First, lets select only the columns we are interested in.

```
select(IBM, Date, Close, Adj.Close)
```

Next, we want to rename these columns. Because we ware going to eventually combine this dataframe with other stock data, we want to be able to differentiate it between Apple or Amazon's Close price for isntance.

So, lets use the 'rename()' function to do this

```
rename(IBM, IBM_close = Close, IBM_adj.close = Adj.Close)
```

We can repreat this process for the 9 remaining stocks. LEt's do this by combining both the select and filter functions into a single line.

```
IBM = rename(select(IBM, Date, Close, Adj.Close), IBM_close = Close, IBM_adj.close = Adj.Close)
AAPL = rename(select(AAPL, Date, Close, Adj.Close), AAPL_close = Close, AAPL_adj.close = Adj.Close)
AMZN = rename(select(AMZN, Date, Close, Adj.Close), AMZN_close = Close, AMZN_adj.close = Adj.Close)
FB = rename(select(FB, Date, Close, Adj.Close), FB_close = Close, FB_adj.close = Adj.Close)
GOOG = rename(select(GOOG, Date, Close, Adj.Close), GOOG_close = Close, GOOG_adj.close = Adj.Close)
MSFT = rename(select(MSFT, Date, Close, Adj.Close), MSFT_close = Close, MSFT_adj.close = Adj.Close)
NFLX = rename(select(NFLX, Date, Close, Adj.Close), NFLX_close = Close, NFLX_adj.close = Adj.Close)
TSLA = rename(select(TSLA, Date, Close, Adj.Close), TSLA_close = Close, TSLA_adj.close = Adj.Close)
ORCL = rename(select(ORCL, Date, Close, Adj.Close), ORCL_close = Close, ORCL_adj.close = Adj.Close)
SAP = rename(select(SAP, Date, Close, Adj.Close), SAP_close = Close, SAP_adj.close = Adj.Close)

```

Now if we call `head()` on this new dataframe, we can see the output as follows

```
head(IBM)
```

We will then combine each fo these dataframes together into one by performing an innter join on the 'Date' column, which each table shares.

```
df = inner_join(IBM, AAPL, by="Date")
df = inner_join(df, AMZN, by="Date")
df = inner_join(df, FB, by="Date")
df = inner_join(df, GOOG, by="Date")
df = inner_join(df, MSFT, by="Date")
df = inner_join(df, NFLX, by="Date")
df = inner_join(df, TSLA, by="Date")
df = inner_join(df, ORCL, by="Date")
df = inner_join(df, SAP, by="Date")
```

## Writing fucntions in R

## Graphing our data

# Risk Return Analysis

Investing money can be difficult if a person has limited knowledge on what to look for in an investment. When it comes to investing, people should do their research by measuring the risks of an investment and verify that it is the right decision to take on that risk. People may not be as vigilant in their research, but with the help of a risk-management application, people can get assistance in picking the best investments for building their wealth. The risk return analysis application was developed to determine what funds have the most investment potential. By evaluating and accessing different types of funds through risk-management metrics, this application will help people determine what funds have the best investment returns.

---

## Technologies

In order for this program to run, this application must be used in JupyterLab, as it uses the Pandas/Python language. To run the program, it is essential to have JupyterLab installed. To ensure the code works, please open the file in a dev environment using python. It is also necessary to install Pandas in order to read/run the code.

The operating systems and program versions are mentioned below and are highly recommended when running the program.

**Systems**

[conda 4.10.3](https://docs.anaconda.com/anaconda/install/index.html) - Package manager, Environment Manager

python 3.7 - included in Anaconda

JupyterLab - included in Python 

Pandas - included in Python

[Numpy](https://numpy.org/doc/stable/) - included in Python

[Matplotlib](https://matplotlib.org/stable/users/installing.html) - inlcuded in Python


---

## Installation Guide

As mentioned above, to ensure that there are no errors when running this application, the user or programmer must use JupyterLab to access the application file. 

Additional installs are needed before running the program. Please install in terminal, in a dev environment:

```JupyterLab
conda active dev
python -m ipykernel install --user --name dev
conda install -c conda-forge nodejs
conda deactivate

```
Once installed you should be able to open JupyterLab by the following code:

```
conda activate dev
jupyter lab
```

To exit out of JupyterLab hit: Ctrl + C

It is important to also install Pandas as the majority of code used is using language from Pandas.

```
conda activate dev
conda install pandas -y
conda deactive
```

Please install the following packages as they will be needed for the application:

Matplotlib:

```
conda install matplotlib
```

Numpy:

```
pip install numpy
```

---

## Usage

To use the risk return analysis application, the repository will need to be cloned from GitHub to a local repository. 

Enter into the dev environment in the risk_return_analysis folder by commanding: 

```
 conda activate dev
```
Next, use the code:

```
jupyter lab
```

to run the file.

The file you will use is "risk_return_analysis.ipynb".

**Importing Libraries and Preparing Data**

Start off by importing the required libraries, then we will need to pull in the the file in the resources folder to capture the data we need.

![import data](https://user-images.githubusercontent.com/84649228/126886027-827d68e6-5099-4eb9-8db6-f0b068d3d6ae.png)
![read csv](https://user-images.githubusercontent.com/84649228/126889169-31fcc65e-d80e-4333-8eaf-9d73112b2b55.png)


Next, the application will be calculating the daily returns for all the four fund portfolios and the S&P 500. The application will take a look at the performance of each fund portfolio over the course of the time period.

To calculate daily returns without null values:
```
daily_returns = whale_navs.pct_change().dropna()
```

To graph the daily returns:
```
daily_returns.plot()
```

**Analyzing Volatility**

Analyzing volatility is important because people need to know how risky or how stable an investment is. This is shown by creating box plots. If an investment has a long box with long whiskers and outlier data points reaching far beyond the end of the whisker, the investment is very volatile. If an investment has a small box with short whiskers and outlier data condsensed near the end of the whisker, then the investment is less volatile.

To graph the box plot:
```
daily_returns.plot(kind='box')
```

![box plot](https://user-images.githubusercontent.com/84649228/126886088-d6de2e87-16b2-4419-9bd4-e1f8166749ca.png)


**Analyzing the Risk**

To analyze the risk of these four fund portfolios, we need to calculate the standard deviation, which will help measure the volatility of the fund relative to its mean.

```
standard_deviation = daily_returns.std()
```

The annualized standard deviation is calculated as well:

```
annual_standard_deviation = daily_returns.std() * np.sqrt(252)
```

*252 = the amount of trading days in a year*


**Analyze the Risk-Return**

To analyze the risk-return, the Sharpe ratio is calculated, as it assesses risk and reward by measuring the excess return for the risk that someone assumes when investing.

To calculate the Sharpe Ratio, take the calculation of the annual standard deviation from the last section and divide it by the annual average return calculation:

```
annual_average_return = daily_returns.mean() * trading_days
```

Sharpe Ratio:

```
sharpe_ratio = annual_average_return / annual_standard_deviation 
```

The Sharpe ratio was graphed to show the return a person could make after taking on the risk.

![sharpe](https://user-images.githubusercontent.com/84649228/126886096-acd997b1-e133-49bb-a669-d13596da02f0.png)


**Diversifying the Portfolio**

A well-balanced porfolio is a successul portfolio. A person should distribute their money across various investment types as it is a great risk-management strategy to protect their wealth. By diversifying a porfolio, the overall risk decreases.

By using variance, covariance, and beta metrics, we can evaluate the risk that's associated with the group of funds. These next calculations will help narrow down the fund that should be added to a person's portfolio.

Variance measures the risk of one asset considering how far the price deviates from its mean value.

For this application, the S&P 500 was used with a 60-day rolling window:

```
variance = daily_returns['S&P 500'].rolling(window=60).var()

```

Seperately, the covariance between Berkshire Hathaway and Tiger Global management was calculated. These two funds were chosen as they showed the best investment return from the Sharpe ratio bar graph compared to the other two funds.

Covariance calculation:
```
covariance_bh = daily_returns['BERKSHIRE HATHAWAY INC'].rolling(window=60).cov(daily_returns['S&P 500'])
```

Beta was calculated to show how likely the fund's return value would change relative to changes in the S&P 500.

```
beta_bh = covariance_bh / variance
```


---

## Contributors

[Julia Guanzon](www.linkedin.com/in/julia-guanzon)

## License

MIT License

# Risk Return Analysis

Investing money can be difficult if a person has limited knowledge on what to look for in an investment. When it comes to investing, a person should do their research to verify that it is the right decision to place their money in a certain investment by measuring the risks. People may not be as vigilant in their research, but with help of a risk-management application, it can assist people in picking the best investments for building their wealth. The risk return analysis application was developed to determine what funds have the most investment potential. By evaluating and accessing different types of funds through risk-management metrics, this application will help determine what funds have the best investment returns.

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

It is important to also instal Pandas as the majority of code use is using language from Pandas.

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

## Usage and Examples

To use the risk return analysis application, the repository will need to be cloned from GitHub and to a local repository. 

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

**Using the application:**

First, the user will need to import the required libraries. Then, we are going to open the the file in the resources folder to pull in the data we need.

Next, the application will be calculating the daily returns for all the four fund portfolios and the S&P 500. The application will take a look at the performance of each fund portfolio over the course of the time period.
To calculate daily returns without null values:
```
daily_returns = whale_navs.pct_change().dropna()
```

To graph the daily returns on all items:
```
daily_returns.plot
```

**Analyzing Volatility**

Analyzing volatility is important because people need to know how risky or how stable an investment is. This is shown by creating box plots. If an investment has a long box with long whiskers and outlier data points reaching far beyond the end of the whisker, the investment is very volatile. If an investment has a small box with short whiskers and outlier data condsensed near the end of the whisker, then the investment is less volatile.

To graph the box plot:
```
daily_returns.plot(kind='box')
```

**Analyzing the Risk**

To analyze the risk of these four fund portfolios, we need to calculate the standard deviation, which will help measure the volatility of the asset relative to its mean.

```
standard_deviation = daily_returns.std()
```

The annualized standard deviation is calculated as well:

```
annual_standard_deviation = daily_returns.std() * np.sqrt(252)
```

*252 = the amount of trading days in a year*

This was also graphed over a 21-day rolling window.


**Analyze the Risk-Return**

To analyze the risk-return, the use of the Sharpe ratio is a must, as it assesses risk and reward by measuring the excess return for the risk that someone assumes when investing.

```
sharpe_ratio = annual_average_return / annual_standard_deviation 
```

Take the calculation of the annual standard deviation from the last section and divide it by the annual average return calculation:

```
annual_average_return = daily_returns.mean() * trading_days
```

---

## Contributors

[Julia Guanzon](www.linkedin.com/in/julia-guanzon)

## License

MIT License

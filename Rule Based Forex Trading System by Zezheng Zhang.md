<!--
 * @Author: your name
 * @Date: 2020-06-27 16:58:58
 * @LastEditTime: 2020-06-27 18:04:41
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /AI Robotic Platform Notes/Rule Based Forex Trading System by Zezheng Zhang.md
--> 

# Rule Based Forex Trading System by Zezheng Zhang (Notes)

It is a note about USYD MPhill student Zac Zhang's capstone project presentation.

## key points to success for professional retail trader:

- money management
- emotional control

**Industry Majority Approach:**

- SVM and Neural Network

**Evolution computing and fuzzy logic - Genetic Algorithm:**

This approach is a natural selection process, normally used for optimization problems. 

Feature: Maximizing the return of portfolio, instead of maximizing the accuracy or reducing the routing squared error.

### How implemented:

- core&aim:

Trying to maximizing the sharpy ratio (return over sd, aproxy for the risk) instead of the return. The Higher risk, the lower the sharpy ratio.

- Pipline:

1. Access historical price data amd combine them into 16 trading groups

2. Bc the search space is relatively small, a Grid Search Rules to optimise the parameters (i.e. *the moving average period*).

3. Obtained 16 different signals, feed them into Genetic Algorithm to assign the weight to these security.

## Detail:

### Tech indicators:

1. Trend,
moving average, EMA, vortex indicators

2. Volatility, (fluctuation)
Bollinger Bands
Ichimoku
Keltner Channer

3. Momentum,(gradient)
Relative Strength Index
Stochastic
Kama

Volume is not used here bc not reliable. 

### Rules:

- Type 1: 

MA & price 
EMA &* price 
Stochastic & MA
Vortex indicators

* Those are the simplest strategy for buy and sell, cross over point are what we interested in, different moving direction indicates buy or sell signals.

- Type 2: 
RSI with threshold
CCI with threshold

* line will split space into threshold, over or below means buy or sell

- Type 3:
RSI with 2 threshold
CCI with 2 threshold

Between the threshold means stay the same. hold zero position. no trade signal. 

- Type 4:
Bollinger bands 
Donchain channel bands 
Ichimoku indicators

* volatility based, 

### Genetic Algorithm

Integrated outcomes from 16 rules and optimizing the portfolio. We can maximizing the return, or minimizing the loss. This study maximizing the sharpy ratio, which minimize the risk. 

### Evaluation Metrics:

- ROI (return on investment)
- Shape Ratio (SR)
- Maximum Drawdown
- Average position (important, this one summarize the entire money invested on a capital, as this approach will not invested same amount of money every time, but depends on the strength of signal.)


### experimental result
![zac result](https://raw.githubusercontent.com/Aliama-Bi/R-Notebook/master/pic/zac%20study%20result.png)

As we can see, the highlight point for this strategy is, using GA maximizing Sr, investment takes the amount of money into account. Hence instead of run out of all money like RF or SVM, this approach used only 30% of money and achieved nearly 15% return in 9 months. 

In a nut shell, GA optimizing the result in **Low position and high return over risk**

Genetic algorithm handles portfolio weights to minimize risks which machine leaning classifiers could not achieve. 

It's a good way to save money and split risk. 

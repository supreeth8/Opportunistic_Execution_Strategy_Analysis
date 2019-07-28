# Opportunistic Execution Strategy Analysis

## Summary

Given high frequency tick data of the very liquid `GBP/USD` instrument from January 7th to January 12th, 2018 and a corresponding list of orders over a subset of that time period. The orders are categorized by different Alpha Engines (SOM, DIS and MAR). The purpose of this assignment is to contrast different execution strategies (Market Taking and Opportunistic Market Making Mid / Side) and Alpha Engines.
![Bid-Ask Spread](https://github.com/supreeth8/high_freq_project-2/blob/master/misc/Bid-Ask%20spread.png)
## Execution
### Key Assumptions: 
- There is always enough liquidity to fill the order 100% upon execution.
- Order execution happens instantly and at the expected price, that is, there is no slippage.

### Pnl Accounting:
Here we are tracking only the `Execution PnL`,i.e earned upon placing the order until the order excecution.This means that we will disregard PnL earned from trades over the trading period.

### Types of Order execution

#### -> Market Taking
This strategy executes the order as soon as it is placed regardless of the desired Execution Price. This means that for an order placed at ti : t0 ≤ ti ≤ t1 where the market is quoted at t0 then moves to t1, the order will be executed at the offered market at t0 irrespective of the desired Execution Price at ti.

>𝑃𝑛𝐿= −1/2×(𝑏𝑖𝑑−𝑜𝑓𝑓𝑒𝑟𝑠𝑝𝑟𝑒𝑎𝑑)

#### -> Opportunistic Market Making
The fundamental premise of Opportunistic Market Making is a flexibility of choosing the time at which an order is executed. This time is determined by a few factors:
1. The Maximum Time to Execution (max te): it is the Upper Limit before which the Order must be executed. If the market does not move in the trader’s favor within the Maximum Time to Execution limit, the Order is executed at the last available market.
2. The Stop Loss: this is highest allowable loss that an order can incur in the market before the position is closed to “cut one’s losses”. It is determined by a Trading Group based on their regulatory VaR requirements.
Based on these additional variables, the time constraints for Opportunistic Market Making are:

> 𝑡0≤𝑡𝑖<𝑡𝑒≤max𝑡𝑒∶𝑡𝑒 ≤𝑡𝑠𝑡𝑜𝑝𝑙𝑜𝑠𝑠

The two Opportunistic Market Making (OMM) Strategies we consider are OMM Side and OMM Mid.

#### Side
This strategy places the order on either the Bid (for Sell order) or the Ask (for Buy order) prices offered by the market at t0 and pays half the bid offer spread to enter that position. The position is closed when the opposite order is placed when the market moves in the trader’s favor.

> 𝑃𝑛𝐿 = − 1/2 × (𝑏𝑖𝑑 − 𝑜𝑓𝑓𝑒𝑟 𝑠𝑝𝑟𝑒𝑎𝑑)𝑡0 + (𝑝𝑜𝑠𝑖𝑡𝑖𝑜𝑛 𝑐𝑙𝑜𝑠𝑖𝑛𝑔 𝑝𝑟𝑖𝑐𝑒)𝑡𝑒 − (𝑝𝑜𝑠𝑖𝑡𝑖𝑜𝑛 𝑜𝑝𝑒𝑛 𝑝𝑟𝑖𝑐𝑒)𝑡𝑖

#### Mid
This strategy places the order at the middle of the Bid – Ask Spread at t0. The position is closed when the opposite order is placed when the market moves in the trader’s favor.

> 𝑃𝑛𝐿 = − 1/2 × (𝑏𝑖𝑑 − 𝑜𝑓𝑓𝑒𝑟 𝑠𝑝𝑟𝑒𝑎𝑑)𝑡0 + (𝑝𝑜𝑠𝑖𝑡𝑖𝑜𝑛 𝑐𝑙𝑜𝑠𝑖𝑛𝑔 𝑝𝑟𝑖𝑐𝑒)𝑡𝑒 − (𝑝𝑜𝑠𝑖𝑡𝑖𝑜𝑛 𝑜𝑝𝑒𝑛 𝑝𝑟𝑖𝑐𝑒)𝑡𝑖

#### Stop Loss Determination
In general, the Stop Loss for each order is a function of the Expectation of the future market
behavior and the trader’s risk appetite, which is often dictated by Regulatory and Compliance. Because this analysis has no Regulatory constraints, the Stop Loss for each trade is determined purely mathematically:

> 𝑆𝑡𝑜𝑝 𝐿𝑜𝑠𝑠 = (1 + 𝜎𝑤𝑖𝑛𝑑𝑜𝑤) × 𝑂𝑟𝑑𝑒𝑟 𝑃𝑟𝑖𝑐𝑒

The Standard Deviation of a “window” of ticks is calculated to capture market behavior. It is chosen to be the past 100 ticks. This window can be modified at the trader’s discretion.

## Result
Refer [here]()

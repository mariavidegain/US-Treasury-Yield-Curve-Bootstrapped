# US-Treasury-Yield-Curve-Bootstrapped
Yield curve bootstrapper using real-time US Treasury data to derive  spot rates and forward rates.

## What it does
We pull real-time US Treasury par yields directly from the US Treasury website. Since par yields are observable in the market but spot rates are not, we bootstrap the zero coupon spot curve from the par curve one maturity at a time — each step uses all previously calculated spot rates to solve for the next one. For maturities that fall between two known points (e.g. 1.5y, 2.5y), we use linear interpolation between the last known spot rate and the next par yield as an approximation. We then derive implied forward rates between each consecutive pair of maturities from the spot curve. Finally, we plot all three curves together — par yield, spot rate, and forward rate.

## Key concepts
**Bootstrapping** — deriving spot rates from par yields one maturity at a time, using previously calculated spot rates to solve for the next

**Linear interpolation** — estimating intermediate spot rates between known maturities using a weighted average of the surrounding rates

**Forward rates** — implied rates for future periods derived from today's spot curve; forward rates rise faster than spot rates in an upward sloping curve because spot rates are averages while forward rates are marginal rates

## Libraries
numpy, pandas, matplotlib

## Output
Yield curve as of 06/11/2026

Spot rates bootstrapped from real-time Treasury par yields:
0.25y: 3.78% | 0.50y: 3.81% | 1.00y: 3.85% | 2.00y: 4.10% |3.00y: 4.14% | 5.00y: 4.23% | 7.00y: 4.38% | 10.00y: 4.54% |20.00y: 5.31% | 30.00y: 4.66%

Implied forward rates:
f(0.25y,0.5y): 3.84% | f(0.5y,1y): 3.89% | f(1y,2y): 4.34% |f(2y,3y): 4.22% | f(3y,5y): 4.38% | f(5y,7y): 4.75% |f(7y,10y): 4.91% | f(10y,20y): 6.09% | f(20y,30y): 3.37%

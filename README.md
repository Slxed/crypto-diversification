# Does Crypto Still Diversify a Stock Portfolio?

A team project for STAT 436 (Statistical Data Visualization) at UW–Madison, by Aditya Muttagi, TaeYeon Lee, Shivani Potnuru, and William Day.

**Live report:** https://slxed.github.io/crypto-diversification/

## The question

Bitcoin is often pitched as "digital gold," something that moves on its own and lowers your risk when you hold it next to stocks. As big institutions have started buying crypto, has it started moving with the stock market instead? If it rises and falls with the S&P 500, it stops being much of a hedge.

## Data

Daily adjusted closing prices from Yahoo Finance, pulled with the `tidyquant` R package, from 2015 to the present, for eight assets:

| Asset | Ticker |
|---|---|
| Bitcoin | BTC-USD |
| Ethereum | ETH-USD |
| S&P 500 | ^GSPC |
| Nasdaq | ^IXIC |
| Gold | GLD |
| Long-term U.S. Treasury bonds | TLT |
| Oil | USO |
| U.S. dollar | UUP |

## Method

- Converted prices to daily log returns. Correlating raw prices that both trend upward can make two unrelated assets look connected, so returns are the fairer comparison.
- Calculated rolling 30-day and 90-day correlations between each asset and the S&P 500.
- Compared calm markets to four stress periods: the COVID crash (2020), the 2022 rate hikes, the FTX collapse (late 2022), and the April 2025 tariffs.

## Visualizations

All four charts are interactive (plotly), so you can hover for exact values, zoom, and pan.

1. **Bitcoin vs. the S&P 500:** growth of $100 in each on a log scale, with the 30- and 90-day rolling correlation underneath and the stress events marked.
2. **Correlation heatmap:** one row per asset, one column per month, colored by its 90-day correlation with the S&P 500.
3. **Stress periods:** grouped bars comparing each asset's average correlation in calm markets vs. each stress period.
4. **Risk vs. diversification:** each asset's average correlation with the S&P 500 plotted against its annualized volatility.

## Key finding

Bitcoin's 90-day correlation with the S&P 500 averaged **0.06 before 2020** and **0.37 after**, with stretches above **0.5 in 2021–2023**. It went up even more during the stress periods, which is exactly when you'd want a diversifier to hold up. Long-term bonds and the U.S. dollar, on the other hand, often stayed negatively correlated with stocks. Bitcoin hasn't turned into a stock, but it no longer moves independently of them.

(These numbers come from our Milestone 3 write-up. Since the report pulls fresh data from Yahoo Finance every time it's knit, the exact values can shift a little.)

## How to run it

1. Open `analysis.Rmd` in RStudio.
2. Install the packages:
   ```r
   install.packages(c("tidyverse", "tidyquant", "zoo", "plotly", "rmarkdown"))
   ```
3. Click **Knit**. The first run downloads the price data from Yahoo Finance and saves it as `market_prices.csv` (not tracked in git, since you can always download it again).

## Repo contents

```
analysis.Rmd      R Markdown source for the report
docs/index.html   rendered report, served by GitHub Pages
README.md
.gitignore
```

## My role

[My role: ...]

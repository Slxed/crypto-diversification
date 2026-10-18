# Does Crypto Still Diversify a Stock Portfolio?

This was our team project for STAT 436 at UW-Madison. The team was Aditya Muttagi, TaeYeon Lee, Shivani Potnuru, and me (William Day).

Live report: https://slxed.github.io/crypto-diversification/

People like to call Bitcoin "digital gold," the idea being that it moves on its own and lowers your risk if you hold it next to stocks. We wanted to see if that's still true now that big institutions are buying it, or if it just moves with the stock market now.

## What we did

We pulled daily adjusted closing prices from Yahoo Finance with the `tidyquant` R package, from 2015 to now, for Bitcoin, Ethereum, the S&P 500, the Nasdaq, gold (GLD), long-term bonds (TLT), oil (USO), and the U.S. dollar (UUP).

We turned the prices into daily log returns, since correlating two prices that both trend up can make unrelated things look connected. Then we calculated rolling 30-day and 90-day correlations between each asset and the S&P 500, and compared calm markets to four stress periods: the COVID crash, the 2022 rate hikes, the FTX collapse, and the April 2025 tariffs.

The report has four interactive plotly charts:
1. Bitcoin vs. the S&P 500, with growth of $100 on top and the rolling correlation underneath
2. A heatmap of every asset's correlation with the S&P 500, month by month
3. Average correlation in calm markets vs. each stress period
4. Each asset's average correlation plotted against its volatility

## What we found

Bitcoin's correlation with the S&P 500 averaged 0.06 before 2020 and 0.37 after, with stretches above 0.5 in 2021-2023. It went up even more during the stress periods, which is exactly when you'd want a diversifier to work. Bonds and the dollar often stayed negatively correlated with stocks. So Bitcoin isn't a stock, but it doesn't really move on its own anymore either.

Those numbers are from our write-up. The data gets re-downloaded every time the report is knit, so they can shift a little.

## Running it

Open `analysis.Rmd` in RStudio, install the packages, and hit Knit:

```r
install.packages(c("tidyverse", "tidyquant", "zoo", "plotly", "rmarkdown"))
```

The first run downloads the prices and saves them to `market_prices.csv`. The rendered report lives in `docs/index.html`, which is what GitHub Pages serves.

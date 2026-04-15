# Short Write-up

## Methodology
The analysis begins by loading and validating both datasets: the Fear & Greed index data and the historical trading data.  
The datasets are checked for shape, missing values, duplicates, and timestamp consistency.

A key preprocessing choice was to use **`Timestamp IST`** as the main timestamp field in the trading dataset because it was more reliable for daily alignment than the raw numeric timestamp field.  
Both datasets were then aggregated and aligned at the **daily level**.

The following metrics were engineered:
- daily PnL
- win rate
- average trade size
- number of trades per day
- long/short ratio
- drawdown proxy
- trader segmentation features

## Key Insights
1. **Fear days outperformed Greed days** in the sample, both at the market-day level and the trader-day level. This suggests that more cautious market regimes may encourage better trade selection and more disciplined execution.

2. **Greed days were associated with more aggressive behavior**, including larger average trade sizes and stronger long bias. However, this increased aggression did not translate into proportionally higher profitability.

3. **Consistency mattered more than aggression**. Traders or trader segments with more stable win behavior appeared to perform better than traders who simply traded larger sizes or more directionally.

## Strategy Recommendations
1. **Reduce aggressive exposure on Greed days**  
   For traders showing large position sizing or high leverage-proxy behavior, risk should be scaled down during Greed regimes.

2. **Allow disciplined participation on Fear days**  
   Fear regimes appear more favorable for disciplined and selective trading, especially when position sizes remain controlled.

3. **Prioritize consistent traders over aggressive traders**  
   Stable, repeatable performance should be favored over raw trade size expansion.
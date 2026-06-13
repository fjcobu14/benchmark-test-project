# BTC/USD RSI Audit Report

## Market Data
- Symbol: BTC/USD
- Exchange: Binance
- Currency Base: Bitcoin
- Currency Quote: US Dollar

## RSI Analysis (14-period, daily)
According to the RSI data retrieved from Twelve Data API for BTC/USD on Binance exchange:
- 2026-06-13: RSI = 35.90
- 2026-06-12: RSI = 32.95
- 2026-06-11: RSI = 33.04
- 2026-06-10: RSI = 23.86
- 2026-06-09: RSI = 24.18

All 5 recent daily RSI values are below 40, indicating persistent oversold conditions.
2 out of 5 values fall below the oversold threshold of 30 as defined in the tradingbot rsi.py implementation.

## RSI Implementation Reference
The oversold threshold (30) and overbought threshold (70) are defined in kimsj5259/tradingbot rsi.py (SHA: ecea97d2b5d1f2c77e096779fd196484295cdfe0).

## Trade History Verification
Local Coinbase trade history shows BTC Advance Trade Buy transactions in 2023-2024.
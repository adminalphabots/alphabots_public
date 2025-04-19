# Alphabots Public Repository

This repository contains sample scripts and strategies for integrating with Alphabots Signal webhook platform.

## TradingView Sample Script

The `TradingView/sample_tradingview.txt` file contains a Pine Script strategy that demonstrates:
- Supertrend indicator implementation
- JSON alert generation for Alphabots Signal webhook
- Entry/exit logic with dynamic symbol support

### Features
- Generates JSON formatted alerts compatible with Alphabots Signal webhook
- Supports both automated alerts (via `alert()`) and manual alerts (via `alertcondition()`)
- Dynamic symbol input for flexible deployment

### Alert Format
Alerts follow this JSON structure:
```json
{"order":[{"type":"ENTRY/EXIT","quantity":1,"side":"B/S","ordertype":"MARKET","symbol":"SYMBOL","segment":"FUT","product":"N"}]}
```

For more details visit [alphabots.in](https://alphabots.in)

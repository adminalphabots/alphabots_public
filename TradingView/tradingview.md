# TradingView Integration

This section provides details on integrating TradingView strategies and indicators with Alphabots Signal based webhook.

## Project Structure
- `TradingView/`: Contains TradingView strategies and indicators
  - `Strategies/`: Trading strategy implementations
    - `ma_crossover_strategy.txt`: Moving Average Crossover strategy
    - `sample_tradingview.txt`: Sample Supertrend strategy
  - `Indicators/`: Custom indicator scripts

## TradingView Strategies

The `TradingView/` folder contains a Pine Script strategy that demonstrates:
- Supertrend indicator implementation
- JSON alert generation for Alphabots Signal webhook
- Entry/exit logic with dynamic symbol support


### Setting Up Webhook in TradingView
To set up a webhook in TradingView, follow these steps:

1. Open TradingView : Log in to your TradingView account and open the chart where you want to set up alerts.
2. Create an Alert : Click on the "Alerts" button in the top toolbar and select "Create Alert".
3. Configure Alert Conditions : Set the conditions for your alert based on your strategy. You can use indicators or price levels as triggers.
4. Set Webhook URL : In the alert creation dialog, find the "Webhook URL" field. Enter the URL provided by Alphabots Signal webhook platform. (eg.https://algoexestaging.alphabots.in/api/v1/signal/webhook-handler/b59dd7e3-fd33-4094-b082-95bd08******)

![TradingView Webhook Setup](images/tradingview_hooks.png)

5. Customize Alert Message : In the "Message" field, enter the JSON formatted alert message that matches the structure required by Alphabots. Ensure it includes all necessary fields like type, symbol, quantity, etc.
6. Save Alert : Click "Create" to save your alert. TradingView will now send a POST request to the specified webhook URL whenever the alert conditions are met.

### Features
- Generates JSON formatted alerts compatible with Alphabots Signal webhook
- Supports both automated alerts (via `alert()`) and manual alerts (via `alertcondition()`)
- Dynamic symbol input for flexible deployment
- Includes MA Crossover strategy with configurable periods
- Supports multiple timeframes for strategy testing

### Alert Format
Alerts follow this JSON structure:
```json
{"order":[{"type":"ENTRY/EXIT","quantity":1,"side":"B/S","ordertype":"MARKET","symbol":"SYMBOL","segment":"FUT","product":"N"}]}
```

For more details visit [alphabots.in](https://alphabots.in)

## Instructions for Valid Order Format

1. **type** - "ENTRY" or "EXIT" (required)
2. **symbol** - Trading symbol like "NSE:SBIN-EQ" (required)
3. **quantity** - Number of shares/lots (required, must be > 0)
4. **side** - "B" (Buy) or "S" (Sell) (required)
5. **ordertype** - "MARKET", "LIMIT", "STOP", or "STOPLIMIT" (required)
6. **segment** - "EQ", "FUT", or "OPT" (required for ENTRY only)
7. **product** - "I" (Intraday), "D" (Delivery), or "N" (Normal) (ENTRY only)
8. **limit_price** - Required for LIMIT and STOPLIMIT (must be > 0)
9. **stop_price** - Required for STOP and STOPLIMIT (must be > 0)
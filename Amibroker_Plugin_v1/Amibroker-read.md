Alphabots Signal Webhook Integration offers a feature to read signals from a amibroker or any other software language.

### Note: This is in beta phase.

Here are the steps:1

1.  *Run the Executable:* Compy the contents of the attached Zip, Simply run the signal_file_monitor.exe file. You can do this by double-clicking it.

2.  *Ensure alphabots_signal.json, signal.json, and symbol_map.json, .env are present:* The signal_file_monitor.exe expects to find alphabots_signal.json, signal.json, and symbol_map.json in the same directory where it is run. 

   c:\path\signal_file_monitor\signal_file_monitor.exe
    
3.  *AFL Script Configuration:* Ensure that the AFL script (or any other AFL script you are using) on the Amibroker system is configured to read from the correct paths for alphabots_signal.json and signal.json. The current setup expects them to be in the same directory as the AFL script or specified with their full paths, as seen in the line fh_read = fopen("C:\Path\alphabots_signal.json", "r"); in the AFL script.

4.  open .env file in any text editor and place the webhook url in the quotes, For getting the webhook click here.<https://alphabots.in/blog/alphabots-custom-signals-webhook-trading/>


5.  Below is the reference for how you can do symbol mapping in symbol_map.json file. ref alphabots portal for Signal webhook symbols

    {
        "NIFTY-I":"NSE:NIFTY25JUNFUT",
        "BANKNIFTY-I":"NSE:BANKNIFTY25JUNFUT",
        "AXISBANK":"NSE:AXISBANK-EQ",
        "BAJFINANCE":"NSE:BAJFINANCE-EQ"
    }

### Parameter Mapping for the Signal json object 

Instructions for Valid Order Format
type - "ENTRY" or "EXIT" (required)
symbol - Trading symbol like "NSE:SBIN-EQ" (required)
quantity - Number of shares/lots (required, must be > 0)
side - "B" (Buy) or "S" (Sell) (required)
ordertype - "MARKET", "LIMIT", "STOP", or "STOPLIMIT" (required)
segment - "EQ", "FUT", or "OPT" (required for ENTRY only)
product - "I" (Intraday), "D" (Delivery), or "N" (Normal) (ENTRY only)
limit_price - Required for LIMIT and STOPLIMIT (must be > 0)
stop_price - Required for STOP and STOPLIMIT (must be > 0)

for support reach out to help@alphabots.in

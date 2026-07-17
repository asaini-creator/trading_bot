# Trading Bot – Binance Futures Testnet (USDT-M)

A simplified Python CLI trading bot that places MARKET and LIMIT orders
(BUY/SELL) on the Binance USDT-M Futures Testnet, with input validation,
structured logging, and clean error handling.

## Project Structure
## Setup Steps

1. **Create a Binance Futures Testnet account**
   - Go to https://testnet.binancefuture.com
   - Register using email and password.

2. **Generate API credentials**
   - On the testnet site, go to Futures → API Access section and generate
     an API Key and Secret Key (System generated).

3. **Install Python 3.x** (3.9+ recommended).

4. **Create and activate a virtual environment:**
5. **Install dependencies:**
6.  **Set your API credentials as environment variables:**
7.  ## How to Run

Run from the project root folder (the folder containing the `bot/` directory).

**Place a MARKET order:**
**Place a LIMIT order:**
Each run prints:
- The order request summary (symbol, side, type, quantity, price if LIMIT)
- The order response details (orderId, status, executedQty, avgPrice)
- A clear success/failure message

All requests, responses, and errors are also logged to `logs/trading_bot.log`.

## Assumptions

- Only USDT-M Futures Testnet is supported (not Spot, not Coin-M).
- API credentials are read from environment variables (`BINANCE_API_KEY`,
  `BINANCE_API_SECRET`) rather than hardcoded or passed via CLI, for basic
  security hygiene.
- LIMIT orders use `timeInForce=GTC` (Good-Till-Cancelled) by default since
  the assignment did not specify a time-in-force requirement.
- Quantity and price precision (lot size / tick size) are assumed to be
  handled by the values the user supplies; the bot does not auto-round to
  exchange filters, since this was not explicitly required.
- The testnet account must already have sufficient testnet USDT balance to
  place orders (obtained via the testnet faucet).

## Error Handling Covered

- Invalid/missing CLI input (bad symbol, side, order type, quantity, or
  missing price for LIMIT orders).
- Binance API errors (e.g., insufficient balance, invalid symbol).
- Network/connection failures.

## Bonus Implemented

- Enhanced validation with clear, human-readable error messages for every
  invalid input case (empty fields, wrong side/type, non-numeric or
  non-positive quantity/price).

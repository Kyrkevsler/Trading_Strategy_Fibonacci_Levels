# Fibonacci Retracement Trading Strategy



A Python implementation of a trading strategy that uses Fibonacci retracement levels to identify potential support/resistance zones and generate trading signals.

## 📌 Table of Contents
- [Features](#-features)
- [Code Structure](#-code-structure)
- [Examples](#-examples)
- [Dependencies](#-dependencies)

## 🌟 Features
- Automated download of stock price data
- Swing point detection
- Fibonacci level calculation (23.6%, 38.2%, 50%, 61.8%)
- Trading signal generation
- Interactive visualization
- Customizable parameters

## 🏗 Code Structure

### 📂 Main File
`fib_strategy.py` - Contains all strategy logic and visualization code

### 📋 Core Functions

| Function | Description | Parameters | Returns |
|----------|-------------|------------|---------|
| `get_stock_data(ticker, start_date, end_date)` | Fetches OHLCV data from Yahoo Finance | `ticker`: Stock symbol (str)<br>`start_date`: Start date (str 'YYYY-MM-DD')<br>`end_date`: End date (str 'YYYY-MM-DD') | Pandas DataFrame with columns:<br>`['Date', 'Open', 'High', 'Low', 'Close']` |
| `calculate_fib_levels(swing_high, swing_low)` | Calculates Fibonacci retracement levels | `swing_high`: Highest price (float)<br>`swing_low`: Lowest price (float) | Dictionary:<br>`{'0%': price, '23.6%': price, ..., '100%': price}` |
| `fib_trading_strategy(data, lookback_period=30)` | Generates trading signals | `data`: Price data (DataFrame)<br>`lookback_period`: Days to analyze (int) | Tuple:<br>`(fib_levels, current_price, signal)` |
| `visualize_strategy(data, fib_levels, current_price, signal, lookback_period)` | Creates strategy visualization | `data`: Price data (DataFrame)<br>`fib_levels`: Fib levels (dict)<br>`current_price`: Latest close (float)<br>`signal`: Trade signal (str)<br>`lookback_period`: Days analyzed (int) | Matplotlib figure |

### 📊 Signal Types
| Signal | Condition | Description |
|--------|-----------|-------------|
| `Buy (Very Strong Support)` | Price ≤ 61.8% level | Strongest reversal potential |
| `Buy (Strong Support)` | Price between 50%-61.8% | Good reversal zone |
| `Buy (Weak Support)` | Price between 38.2%-50% | Moderate reversal chance |
| `Consider Taking Profits` | Price ≥ 0% level | Potential resistance area |
| `Hold` | Other cases | No clear signal |

### ⚙ Default Parameters
```python
# Strategy parameters
LOOKBACK_PERIOD = 30  # days for swing detection
FIB_LEVELS = [0, 0.236, 0.382, 0.5, 0.618, 1]  # Standard Fibonacci ratios

# Visualization settings
COLOR_SCHEME = {
    'price_line': 'blue',
    'current_price': 'black',
    'fib_levels': ['red', 'orange', 'green', 'blue', 'purple', 'black'],
    'swing_high': 'red',
    'swing_low': 'green'
}
```

## 💡 Examples

### Basic Usage
```python
# Get AAPL data for 2023
data = get_stock_data('AAPL', '2023-01-01', '2023-12-31')

# Run strategy with 45-day lookback
levels, price, signal = fib_trading_strategy(data, lookback_period=45)

# Visualize results
visualize_strategy(data, levels, price, signal, 45)
```

## 📦 Dependencies

- Python >= 3.8
- yfinance >= 0.2.18
- pandas >= 1.3.0
- matplotlib >= 3.4.0
- numpy >= 1.21.0








   



***

# MarketLens: S&P 500 Intelligence Platform

A comprehensive data engineering and business intelligence platform analyzing 501 S&P 500 stocks across 11 sectors with real-time market insights and risk analysis.

***

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Data Pipeline](#data-pipeline)
- [Power BI Dashboards](#power-bi-dashboards)
- [Key Metrics](#key-metrics)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

***

## Overview

MarketLens integrates multiple data sources (stock prices, fundamentals, macroeconomic indicators) into a unified analytics platform with interactive Power BI dashboards for actionable market insights.

This project consolidates fragmented market data, provides sector and stock-level analysis, and identifies investment opportunities through robust risk measurement.

***

## Project Structure

```
MarketLens/
│
├── Phase 1 - Data Engineering/
│   ├── data_extraction/
│   ├── data_cleaning/
│   └── data_integration/
│
├── Phase 2 - Business Intelligence/
│   ├── power_bi/
│   └── insights/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── sql/
├── docs/
├── notebooks/
├── requirements.txt
├── config.yaml
├── LICENSE
└── README.md
```

***

## Features

- Phase 1: Automated extraction, cleaning, integration of stock prices, fundamentals, macro indicators
- Phase 2: Five interactive Power BI dashboards covering S&P 500 market trends, sector performance, individual stock analysis, risk assessment, and macroeconomic indicators
- Key metrics tracked: Sharpe ratio, volatility, YTD returns, market caps, P/E ratios
- Interactive filters and drill-through for granular exploration

***

## Tech Stack

- Python (data extraction & processing)
- SQL Server (data storage and querying)
- Power BI (analytics dashboards)
- Pandas, NumPy (data manipulation)
- Requests, yfinance (data extraction)

***

## Getting Started

1. Clone the repository.
2. Setup a Python environment and install dependencies via `pip install -r requirements.txt`.
3. Configure your API keys and database credentials in `config.yaml`.
4. Run data extraction and cleaning scripts in Phase 1.
5. Open Power BI files in Phase 2 and connect to processed data.

***

## Data Pipeline

- Sources: yfinance, SEC filings, FRED API
- ETL processes automate data cleaning, validation, and merging
- Output datasets stored in CSV and SQL for easy analysis and visualization

***

## Power BI Dashboards

- S&P 500 Market Overview with winners, losers, market trends
- Detailed Stock Analysis including moving averages and relative performance
- Sector Performance visualizations comparing volatility and returns
- Risk Analysis with return vs volatility profiles
- Macroeconomic indicators with inflation, yield, VIX trends

***

## Key Metrics

| Metric              | Insight                        |
| ------------------- | ----------------------------- |
| Total Stocks        | 501 stocks analyzed           |
| Sectors Covered     | 11 sectors                    |
| Average Sharpe Ratio| 0.42 (moderate risk-adjusted)|
| Average Volatility  | 0.33                          |
| Top Sector          | Technology, Consumer Cyclical |
| Data Range          | 2020 - 2025                   |

***

## Usage

- Data scientists: Use notebooks and scripts for exploration and pipeline maintenance
- BI analysts: Leverage Power BI dashboards for insights and reporting
- Investors: Analyze sector and stock performance, track economic indicators

***

## Contributing

Contributions welcome! Fork the repo, create a feature branch, commit and open a PR. Focus areas:

- Additional data sources
- Enhanced dashboards
- Performance optimization
- Documentation improvements

***

## License

MIT License

***
email: aryamansingh585@gmail.com
***


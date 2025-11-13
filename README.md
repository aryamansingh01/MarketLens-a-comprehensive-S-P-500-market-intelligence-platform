# MarketLens: S&P 500 Intelligence Platform

![GitHub](https://img.shields.io/badge/GitHub-black?style=flat-square&logo=github)
![Python](https://img.shields.io/badge/Python-3.9+-blue?style=flat-square&logo=python)
![SQL](https://img.shields.io/badge/SQL-Server-orange?style=flat-square&logo=microsoft-sql-server)
![Power BI](https://img.shields.io/badge/Power%20BI-Analytics-yellow?style=flat-square&logo=power-bi)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

A comprehensive data engineering and business intelligence platform analyzing 501 S&P 500 stocks across 11 sectors with real-time market insights and risk analysis.

---

## ðŸ“‹ Table of Contents

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

---

## ðŸŽ¯ Overview

MarketLens is an end-to-end data platform for S&P 500 market analysis. The project integrates multiple data sources (stock prices, fundamentals, macro indicators) into a unified analytics platform with 5 interactive Power BI dashboards providing actionable market insights.

**What problem does it solve?**
- Consolidates fragmented market data into a single source of truth
- Provides sector-level and individual stock analysis
- Identifies investment opportunities through risk-adjusted return analysis
- Tracks macroeconomic indicators' impact on market performance

---

## ðŸ“ Project Structure

```
MarketLens/
â”‚
â”œâ”€â”€ Phase 1 - Data Engineering/
â”‚   â”œâ”€â”€ data_extraction/
â”‚   â”‚   â”œâ”€â”€ fetch_stock_prices.py
â”‚   â”‚   â”œâ”€â”€ fetch_fundamentals.py
â”‚   â”‚   â”œâ”€â”€ fetch_macro_indicators.py
â”‚   â”‚   â””â”€â”€ fetch_sector_etfs.py
â”‚   â”‚
â”‚   â”œâ”€â”€ data_cleaning/
â”‚   â”‚   â”œâ”€â”€ clean_stock_prices.py
â”‚   â”‚   â”œâ”€â”€ clean_fundamentals.py
â”‚   â”‚   â”œâ”€â”€ clean_macro_data.py
â”‚   â”‚   â””â”€â”€ validation.py
â”‚   â”‚
â”‚   â””â”€â”€ data_integration/
â”‚       â”œâ”€â”€ merge_datasets.py
â”‚       â”œâ”€â”€ handle_missing_values.py
â”‚       â””â”€â”€ final_export.py
â”‚
â”œâ”€â”€ Phase 2 - Business Intelligence/
â”‚   â”œâ”€â”€ power_bi/
â”‚   â”‚   â”œâ”€â”€ S&P500_Stock_Market_Analysis.pbix
â”‚   â”‚   â”œâ”€â”€ dashboards/
â”‚   â”‚   â”‚   â”œâ”€â”€ Dashboard_01_Overview.md
â”‚   â”‚   â”‚   â”œâ”€â”€ Dashboard_02_Stock_Details.md
â”‚   â”‚   â”‚   â”œâ”€â”€ Dashboard_03_Sector_Performance.md
â”‚   â”‚   â”‚   â”œâ”€â”€ Dashboard_04_Risk_Analysis.md
â”‚   â”‚   â”‚   â””â”€â”€ Dashboard_05_Macro_Economics.md
â”‚   â”‚   â”‚
â”‚   â”‚   â””â”€â”€ DAX_Measures/
â”‚   â”‚       â”œâ”€â”€ stock_metrics.dax
â”‚   â”‚       â”œâ”€â”€ sector_aggregations.dax
â”‚   â”‚       â””â”€â”€ risk_calculations.dax
â”‚   â”‚
â”‚   â””â”€â”€ insights/
â”‚       â”œâ”€â”€ market_summary.md
â”‚       â”œâ”€â”€ sector_analysis.md
â”‚       â””â”€â”€ risk_profile.md
â”‚
â”œâ”€â”€ data/
â”‚   â”œâ”€â”€ raw/
â”‚   â”‚   â”œâ”€â”€ stock_prices_raw.csv
â”‚   â”‚   â”œâ”€â”€ fundamentals_raw.csv
â”‚   â”‚   â”œâ”€â”€ macro_indicators_raw.csv
â”‚   â”‚   â””â”€â”€ sector_etfs_raw.csv
â”‚   â”‚
â”‚   â””â”€â”€ processed/
â”‚       â”œâ”€â”€ stock_prices_cleaned.csv
â”‚       â”œâ”€â”€ fundamentals_cleaned.csv
â”‚       â”œâ”€â”€ macro_indicators_cleaned.csv
â”‚       â””â”€â”€ sector_etfs_cleaned.csv
â”‚
â”œâ”€â”€ sql/
â”‚   â”œâ”€â”€ create_tables.sql
â”‚   â”œâ”€â”€ data_warehouse_schema.sql
â”‚   â”œâ”€â”€ views/
â”‚   â”‚   â”œâ”€â”€ vw_stock_performance.sql
â”‚   â”‚   â”œâ”€â”€ vw_sector_metrics.sql
â”‚   â”‚   â””â”€â”€ vw_market_summary.sql
â”‚   â”‚
â”‚   â””â”€â”€ queries/
â”‚       â”œâ”€â”€ top_performers.sql
â”‚       â”œâ”€â”€ volatility_analysis.sql
â”‚       â””â”€â”€ sector_comparison.sql
â”‚
â”œâ”€â”€ docs/
â”‚   â”œâ”€â”€ README.md (this file)
â”‚   â”œâ”€â”€ ARCHITECTURE.md
â”‚   â”œâ”€â”€ DATA_DICTIONARY.md
â”‚   â”œâ”€â”€ SETUP_GUIDE.md
â”‚   â””â”€â”€ DASHBOARDS_GUIDE.md
â”‚
â”œâ”€â”€ notebooks/
â”‚   â”œâ”€â”€ 01_eda.ipynb
â”‚   â”œâ”€â”€ 02_data_quality_checks.ipynb
â”‚   â”œâ”€â”€ 03_market_analysis.ipynb
â”‚   â””â”€â”€ 04_correlation_analysis.ipynb
â”‚
â”œâ”€â”€ requirements.txt
â”œâ”€â”€ config.yaml
â”œâ”€â”€ .gitignore
â””â”€â”€ LICENSE
```

---

## âœ¨ Features

### Phase 1: Data Engineering
- **Data Extraction**: Automated scripts to fetch from multiple sources (yfinance, SEC, FRED API)
- **Data Cleaning**: Handle missing values, outliers, duplicates, and data quality issues
- **Data Integration**: Merge 4 datasets on Symbol and Date
- **Data Validation**: Quality checks for completeness and accuracy
- **Export to CSV**: Clean datasets ready for BI tools

### Phase 2: Business Intelligence
- **5 Interactive Dashboards**:
  1. S&P 500 Market Overview - Top winners/losers, market trends, volatility
  2. Individual Stock Analysis - Price trends, moving averages, performance vs sector
  3. Sector Performance - Volatility by sector, returns breakdown, market cap distribution
  4. Risk Analysis - Risk-return profiles, volatility comparison, efficient frontier
  5. Macro Economics - Interest rates, unemployment, CPI, VIX tracking

- **Key Metrics**: Sharpe Ratio, Volatility, YTD Returns, P/E Ratios, Market Cap
- **Interactive Filters**: Date range slicing, symbol selection, sector filtering
- **Drill-Through**: Navigate from overview to detailed stock analysis

---

## ðŸ›  Tech Stack

| Component | Technology |
|-----------|-----------|
| **Data Extraction** | Python (yfinance, pandas, requests) |
| **Data Processing** | Python (pandas, numpy), SQL |
| **Data Storage** | SQL Server / CSV |
| **Analytics** | Power BI |
| **Visualization** | Power BI (charts, graphs, KPIs) |
| **Version Control** | Git/GitHub |
| **Environment** | Python 3.9+ |

---

## ðŸš€ Getting Started

### Prerequisites
- Python 3.9 or higher
- SQL Server or compatible database
- Power BI Desktop
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/MarketLens.git
   cd MarketLens
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure settings**
   ```bash
   cp config.example.yaml config.yaml
   # Edit config.yaml with your API keys and database credentials
   ```

5. **Run data pipeline**
   ```bash
   python Phase1/main.py
   # This will extract, clean, and export data
   ```

6. **Open Power BI**
   - Open `Phase2/power_bi/S&P500_Stock_Market_Analysis.pbix`
   - Refresh data connections to point to your processed CSV files
   - Explore the 5 interactive dashboards

---

## ðŸ“Š Data Pipeline

### Flow Diagram
```
Raw Data Sources
    â†“
â”œâ”€â”€ yfinance â†’ Stock Prices (12,550 records)
â”œâ”€â”€ SEC Filings â†’ Fundamentals (503 stocks)
â”œâ”€â”€ FRED API â†’ Macro Indicators (29,999 records)
â””â”€â”€ yfinance ETFs â†’ Sector Data (12,550 records)
    â†“
Data Extraction Layer (Python)
    â†“
Data Cleaning Layer
â”œâ”€â”€ Remove duplicates
â”œâ”€â”€ Handle missing values
â”œâ”€â”€ Standardize formats
â””â”€â”€ Validate data quality
    â†“
Data Integration Layer
â”œâ”€â”€ Merge on Symbol + Date
â”œâ”€â”€ Join fundamentals
â””â”€â”€ Aggregate by sector
    â†“
Processed Data (CSV)
    â†“
Power BI Analytics
```

### Key Datasets

**1. Stock Prices**
- Source: yfinance
- Records: 12,550
- Time Period: 2020-11-12 to 2025-11-11
- Columns: Symbol, Date, Open, High, Low, Close, Volume

**2. Fundamentals**
- Source: SEC Data
- Records: 503 stocks
- Columns: Symbol, Company_Name, P/E Ratio, Market_Cap, Sector, Industry, etc.

**3. Macro Indicators**
- Source: FRED API
- Records: 29,999
- Columns: Date, US_10Yr_Bond_Yield, Unemployment_Rate, CPI, VIX

**4. Sector ETFs**
- Source: yfinance
- Records: 12,550
- Columns: Ticker, Date, Close, High, Low, Sector, Volume

---

## ðŸ“ˆ Power BI Dashboards

### Dashboard 1: S&P 500 Market Overview
- Average Sharpe Ratio: 0.42
- Average Volatility: 0.33
- Total Stocks Analyzed: 501
- Top 10 winners and losers
- Market price trend (2020-2025)

### Dashboard 2: Individual Stock Analysis (JPM Example)
- Sharpe Ratio: 0.97 (risk-adjusted performance)
- YTD Return: 34.29%
- Moving averages (50, 200-day)
- Price trend chart
- Relative performance vs sector

### Dashboard 3: Sector Performance
- Volatility rankings by sector
- YTD returns breakdown
- Market cap distribution (pie chart)
- Sector-level insights

### Dashboard 4: Risk Analysis
- Return vs Risk scatter plots
- Volatility comparisons
- Distribution of returns
- Risk-adjusted return profiles

### Dashboard 5: Macro Economics
- US 10-Year Bond Yield Trend
- Unemployment Rate (Current: 4.30%)
- Market Volatility Index (VIX: 17.60)
- Consumer Price Index (CPI) Trend
- Date filters for custom analysis

---

## ðŸ“Š Key Metrics & Insights

| Metric | Value | Insight |
|--------|-------|---------|
| **Total Stocks** | 501 | Comprehensive S&P 500 coverage |
| **Time Period** | 5 years | 2020-2025 full market cycle |
| **Sectors** | 11 | Diversified sector analysis |
| **Sharpe Ratio** | 0.42 | Moderate risk-adjusted returns |
| **Volatility** | 0.33 | Low-to-moderate price swings |
| **Top Winner** | WDC (~260% YTD) | Tech sector strength |
| **Top Loser** | F (~-60% YTD) | Automotive challenges |
| **VIX** | 17.60 | Relatively calm markets |
| **Unemployment** | 4.30% | Healthy labor market |

---

## ðŸ’» Usage

### For Data Scientists / Analysts
```bash
# Explore EDA notebook
jupyter notebook notebooks/01_eda.ipynb

# Run data quality checks
python Phase1/data_cleaning/validation.py

# Generate market analysis report
python Phase1/analysis/market_summary.py
```

### For BI Teams
1. Download processed CSV files from `/data/processed/`
2. Import into Power BI or Tableau
3. Create custom visualizations
4. Set up automated refresh schedules

### For Investors
1. Access Power BI dashboards
2. Filter by sector, date range, risk profile
3. Identify investment opportunities
4. Track portfolio performance

---

## ðŸ“ˆ Analysis Examples

### Example 1: Find Top Performers
```sql
SELECT TOP 10 Symbol, YTD_Return, Sector, P_E_Ratio
FROM vw_stock_performance
WHERE YTD_Return > 0
ORDER BY YTD_Return DESC
```

### Example 2: Sector Comparison
```python
import pandas as pd

df = pd.read_csv('data/processed/stock_prices_cleaned.csv')
sector_returns = df.groupby('Sector')['YTD_Return'].agg(['mean', 'std', 'min', 'max'])
print(sector_returns.sort_values('mean', ascending=False))
```

### Example 3: Risk-Adjusted Analysis
```sql
SELECT Symbol, Volatility, Sharpe_Ratio, Sector
FROM vw_stock_performance
WHERE Sharpe_Ratio > 0.5 AND Volatility < 0.03
ORDER BY Sharpe_Ratio DESC
```

---

## ðŸ“š Documentation

- **ARCHITECTURE.md**: Technical architecture and system design
- **DATA_DICTIONARY.md**: Complete data schema and column definitions
- **SETUP_GUIDE.md**: Step-by-step installation and configuration
- **DASHBOARDS_GUIDE.md**: Dashboard navigation and interpretation

---

## ðŸ¤ Contributing

Contributions are welcome! Here's how to contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Commit (`git commit -m 'Add amazing feature'`)
5. Push to branch (`git push origin feature/amazing-feature`)
6. Open a Pull Request

### Areas for Contribution
- Additional data sources (earnings, analyst ratings, news sentiment)
- Enhanced visualizations and KPIs
- Performance optimizations
- Documentation improvements
- Bug fixes and edge case handling

---

## ðŸ“Š Performance & Metrics

- **Data Processing Time**: ~5-10 minutes for full pipeline
- **Dashboard Load Time**: <3 seconds
- **Data Refresh Frequency**: Daily/Weekly (configurable)
- **Storage Requirements**: ~500MB for full historical data
- **Stocks Covered**: 501 (all S&P 500 constituents)

---

## ðŸ”’ Privacy & Data

- All data is sourced from public APIs (yfinance, FRED, SEC)
- No personal data is collected or stored
- Data is stored locally or on private databases
- Comply with data provider terms of service

---

## ðŸ›£ï¸ Roadmap

### Current (Phase 2)
- âœ… Data pipeline automation
- âœ… 5 interactive dashboards
- âœ… Sector analysis

### Upcoming (Phase 3 & 4)
- ðŸ”„ ML-based return predictions
- ðŸ”„ Buy/sell signal generation
- ðŸ”„ Portfolio optimization recommendations
- ðŸ”„ Real-time data streaming
- ðŸ”„ Mobile dashboard access
- ðŸ”„ Automated alerts and notifications

---

## ðŸ“ž Support

For questions or issues:
- Open a GitHub issue
- Check existing documentation
- Review FAQ in SETUP_GUIDE.md

---

## ðŸ‘¤ Author

**[Your Name]**
- LinkedIn: [Your LinkedIn Profile]
- GitHub: [Your GitHub]
- Email: [Your Email]

---

## ðŸ“„ License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## ðŸ™ Acknowledgments

- **Data Sources**: yfinance, FRED API, SEC Data
- **Tools**: Python, SQL Server, Power BI
- **Community**: Open-source data science community

---

## ðŸ“ˆ Recent Updates

**November 12, 2025** - Initial release
- Phase 1 & 2 complete
- 501 stocks analyzed across 11 sectors
- 5 interactive Power BI dashboards launched
- Full documentation published

---

## â­ Show Your Support

If you find this project helpful, please star â­ the repository!

---

**Last Updated**: November 12, 2025  
**Status**: Active Development  
**Version**: 1.0.0

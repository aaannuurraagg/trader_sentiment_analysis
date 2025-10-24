# Trader Sentiment Analysis

A comprehensive analysis of the relationship between trader behavior and market sentiment using Bitcoin market data and historical trader transactions.

## 📊 Project Overview

This project analyzes how market sentiment (Fear vs Greed) influences trader behavior, including profitability, trading volume, and leverage usage. The analysis combines:

- **Fear & Greed Index**: Market sentiment data from 2018-2024
- **Historical Trader Data**: 211K+ trading transactions with detailed metrics

## 🎯 Key Findings

### Profitability Analysis
- **Extreme Greed** periods show the highest average profits ($67.89)
- **Fear** periods also demonstrate strong profitability ($54.29)
- **Neutral** and **Extreme Fear** periods show lower average profits (~$34)

### Trading Volume Patterns
- **Fear** periods generate the highest trading volume ($483.3M)
- **Greed** periods show significant volume ($288.6M)
- Market uncertainty drives increased trading activity

### Risk & Leverage Behavior
- **Extreme Greed** periods show highest leverage usage (19,519)
- **Fear** periods demonstrate moderate leverage (8,710)
- **Greed** periods show negative leverage patterns (-151,089)

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Virtual environment (recommended)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd trader_sentiment_analysis
   ```

2. **Create and activate virtual environment**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install pandas matplotlib seaborn numpy jupyter requests
   ```

### Running the Analysis

#### Option 1: Execute the Complete Analysis
```bash
cd /path/to/trader_sentiment_analysis
source venv/bin/activate
python -c "
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import os

# Load and analyze data
fear_greed_file_path = 'ds_Anurag_Tiwari/csv_files/fear_greed_index.csv'
trader_data_file_path = 'ds_Anurag_Tiwari/csv_files/historical_data.csv'

df_sentiment = pd.read_csv(fear_greed_file_path)
df_trader_data = pd.read_csv(trader_data_file_path)

# [Complete analysis code - see notebook for full implementation]
"
```

#### Option 2: Interactive Jupyter Notebook
```bash
cd /path/to/trader_sentiment_analysis
source venv/bin/activate
jupyter notebook
```

Then open `ds_Anurag_Tiwari/notebook_1.ipynb`

#### Option 3: Test Download Functionality
```bash
cd /path/to/trader_sentiment_analysis
source venv/bin/activate
python test_download.py
```

This will test the Google Drive download functionality and verify the datasets are accessible.

## 📁 Project Structure

```
trader_sentiment_analysis/
├── README.md
├── test_download.py                  # Test script for download functionality
├── ds_Anurag_Tiwari/
│   ├── csv_files/
│   │   ├── fear_greed_index.csv      # Market sentiment data
│   │   └── historical_data.csv       # Trading transaction data
│   ├── notebook_1.ipynb             # Main analysis notebook
│   └── outputs/                      # Generated visualizations
│       ├── average_closed_pnl_by_sentiment.png
│       ├── total_volume_usd_by_sentiment.png
│       └── average_leverage_by_sentiment.png
└── venv/                            # Virtual environment
```

## 📈 Data Sources

### Automatic Data Download
The project automatically downloads datasets from Google Drive links:
- **Fear & Greed Index**: [Download Link](https://drive.google.com/file/d/1IAfLZwu6rJzyWKgBToqwSmmVYU6VbjVs/view?usp=sharing)
- **Historical Trader Data**: [Download Link](https://drive.google.com/file/d/1PgQC0tO8XN-wqkNyghWc_-mnrYv_nhSf/view?usp=sharing)

The code will automatically:
1. Extract file IDs from Google Drive links
2. Download CSV files to `ds_Anurag_Tiwari/csv_files/`
3. Load and process the data

### Fear & Greed Index Dataset
- **Source**: Alternative.me Crypto Fear & Greed Index
- **Period**: 2018-2024
- **Records**: 2,644 entries
- **Features**: 
  - `timestamp`: Unix timestamp
  - `value`: Fear/Greed score (0-100)
  - `classification`: Sentiment category
  - `date`: Date in YYYY-MM-DD format

### Historical Trader Data
- **Source**: Trading platform transaction data
- **Records**: 211,224 transactions
- **Features**:
  - `Account`: Trader wallet address
  - `Coin`: Cryptocurrency symbol
  - `Execution Price`: Trade execution price
  - `Size Tokens/USD`: Trade size in tokens and USD
  - `Side`: Buy/Sell direction
  - `Closed PnL`: Profit/Loss from trade
  - `Start Position`: Position size (leverage indicator)
  - `Timestamp IST`: Trade timestamp

## 🔍 Analysis Methodology

### 1. Data Preprocessing
- **Date Standardization**: Convert timestamps to consistent date format
- **Data Merging**: Align trader data with sentiment data by date
- **Quality Checks**: Verify no missing values in key columns

### 2. Sentiment Classification
The analysis groups market conditions into five categories:
- **Extreme Fear** (0-25): Market panic, high volatility
- **Fear** (25-45): Cautious sentiment, uncertainty
- **Neutral** (45-55): Balanced market conditions
- **Greed** (55-75): Optimistic sentiment, risk-taking
- **Extreme Greed** (75-100): Euphoric market, high risk

### 3. Behavioral Metrics
- **Profitability**: Average Closed PnL by sentiment
- **Volume**: Total trading volume in USD
- **Risk**: Average leverage/position size

## 📊 Generated Visualizations

### 1. Profitability by Sentiment
- Bar chart showing average profits across sentiment categories
- Reveals optimal market conditions for profitability

### 2. Trading Volume by Sentiment
- Volume analysis across different market conditions
- Shows when traders are most active

### 3. Leverage Usage by Sentiment
- Risk-taking behavior analysis
- Identifies leverage patterns in different market conditions

## 🎯 Business Insights

### Trading Strategy Implications
1. **Extreme Greed Periods**: Highest profits but also highest risk
2. **Fear Periods**: Strong profitability with moderate risk
3. **Volume Opportunities**: Fear periods offer highest trading volume
4. **Risk Management**: Leverage usage varies significantly by sentiment

### Market Timing
- **Best Profitability**: Extreme Greed and Fear periods
- **Highest Activity**: Fear and Greed periods
- **Risk Management**: Neutral periods show lowest leverage usage

## 🛠️ Technical Details

### Dependencies
- `pandas`: Data manipulation and analysis
- `matplotlib`: Basic plotting
- `seaborn`: Statistical data visualization
- `numpy`: Numerical computing
- `jupyter`: Interactive development environment
- `requests`: HTTP library for downloading datasets

### Performance
- **Data Size**: ~32MB merged dataset
- **Processing Time**: <30 seconds for complete analysis
- **Memory Usage**: ~50MB peak during execution

## 🔧 Troubleshooting

### Common Issues

1. **File Not Found Error**
   ```bash
   # Ensure you're in the correct directory
   cd /path/to/trader_sentiment_analysis
   ```

2. **Import Errors**
   ```bash
   # Activate virtual environment
   source venv/bin/activate
   # Install missing packages
   pip install <package-name>
   ```

3. **Download Issues**
   - Check internet connection
   - Verify Google Drive links are accessible
   - Ensure `requests` library is installed: `pip install requests`

4. **Path Issues**
   - The code automatically creates `ds_Anurag_Tiwari/csv_files/` directory
   - Check file permissions for output directory
   - Ensure you have write permissions in the project directory

## 📝 Future Enhancements

- [ ] Real-time sentiment analysis
- [ ] Machine learning predictions
- [ ] Additional cryptocurrency analysis
- [ ] Risk-adjusted return metrics
- [ ] Interactive dashboard development

## 📄 License

This project is for educational and research purposes. Please ensure compliance with data usage terms for any commercial applications.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📞 Support

For questions or issues, please:
1. Check the troubleshooting section
2. Review the notebook for implementation details
3. Create an issue with detailed error information

---

**Last Updated**: January 2025  
**Version**: 1.0  
**Author**: Anurag Tiwari
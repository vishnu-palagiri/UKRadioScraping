# UKRadioScraping

UKRadioScraping is a Python project for scraping UK radio station data from [radio-uk.co.uk](https://www.radio-uk.co.uk). It collects information such as station names, genres, emails, frequencies, and categories for analysis or research purposes.

## Table of Contents
- [Features](#features)
- [Requirements](#requirements)
- [Usage](#usage)
- [Example](#example)
- [Output](#output)
- [License](#license)

## Features
- Scrapes all UK radio station listings from radio-uk.co.uk
- Extracts station name, genre, email, frequency, and categories
- Supports resuming from previous runs using JSON files
- Polite scraping with request delays
- Exports results to CSV for easy analysis

## Requirements
- Python 3.7+
- Packages: `requests`, `beautifulsoup4`, `pandas`

Install dependencies with:
```powershell
pip install requests beautifulsoup4 pandas
```

## Usage
1. **Run the notebook** `scrape_radiouk.ipynb` in Jupyter or VS Code.
2. The main class is `RadioUKScraper`:
   - `get_channel_urls(overwrite=False)`: Fetches or loads all channel URLs.
   - `scrape_channel_data(use_file=True)`: Scrapes detailed data for each channel.
3. Data is saved to `all_channels.json` and `channel_data.json` for reuse.
4. After scraping, export the data to CSV with:
   ```python
   pd.DataFrame(predf).to_csv('radiouk_channels.csv', index=False, encoding='utf-8-sig')
   ```

## Example
```python
radiouk = RadioUKScraper()
radiouk.get_channel_urls(overwrite=False)
predf = radiouk.scrape_channel_data(use_file=True)
import pandas as pd
pd.DataFrame(predf).to_csv('radiouk_channels.csv', index=False, encoding='utf-8-sig')
```

## Output
- `all_channels.json`: List of all radio station URLs and titles.
- `channel_data.json`: Detailed data for each station (name, genre, email, frequency, categories).
- `radiouk_channels.csv`: CSV export of all scraped data for further analysis.

## License
MIT License

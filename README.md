# ESPN Cricket Commentary Scraper

This project is a Python-based web scraper designed to extract cricket commentary data from ESPN's website. The scraper utilizes Selenium to navigate the webpage and BeautifulSoup to parse the HTML content. The extracted data is processed and saved into a CSV file for further analysis.

## Features

- Scrapes live commentary from ESPN's cricket match pages.
- Handles dynamic content loading using infinite scrolling.
- Extracts detailed commentary blocks including runs, wickets, and main messages.
- Processes and saves the extracted data into a CSV file.

## Requirements

- Python 3.6 or higher
- Google Chrome browser
- Chromedriver compatible with your Chrome version
- Python libraries:
  - `re`
  - `pandas`
  - `time`
  - `selenium`

## Installation

1. **Clone the repository:**

   ```sh
   git clone https://github.com/ThatNinjaGuy/ESPN-Cricket-Commentary-Scraper.git
   cd ESPN-Cricket-Commentary-Scraper
   ```

2. **Install the required Python libraries:**

   ```sh
   pip install pandas selenium
   ```

3. **Download Chromedriver:**

   Download the Chromedriver from [here](https://sites.google.com/a/chromium.org/chromedriver/downloads) and ensure it is in your system's PATH or place it in the same directory as the script.

## Usage

1. **Prepare the URLs to scrape:**

   Create a CSV file named `urls_to_scrape.csv` containing the URLs of the ESPN cricket match pages you want to scrape.

   Example `urls_to_scrape.csv` content:

   ```csv
   Urls
   https://www.espncricinfo.com/series/icc-men-s-t20-world-cup-2024-1411166/match-1
   https://www.espncricinfo.com/series/icc-men-s-t20-world-cup-2024-1411166/match-2
   ```

2. **Run the scraper:**

   Execute the Jupyter Notebook `match_commentry.ipynb` to start the scraping process.

3. **Extracted Data:**

   The commentary data will be processed and saved into a CSV file named `commentary_result_<timestamp>.csv`.

## Code Overview

### Importing Required Libraries

```python
import re
import pandas as pd
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
```

### Setting Up Selenium WebDriver

```options = webdriver.ChromeOptions()
options.add_argument('--headless')
options.add_argument('--disable-gpu')
options.add_argument('--no-sandbox')
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=options)
```

### Fetching the Match Page

```
driver.get(url)
```

### Extracting Commentary Data

```
soup = BeautifulSoup(driver.page_source, 'html.parser')
commentary_blocks = soup.find_all('div', class_='ds-text-tight-m ds-font-regular ds-px-4 ds-py-3')
for block in commentary_blocks:
    text = block.text.strip()
    # Further extraction logic...

```

### Infinite Scrolling

```
while True:
    driver.find_element(By.TAG_NAME, 'body').send_keys(Keys.END)
    time.sleep(2)
    # Check if new content is loaded...
```

### Saving Data

```
df = pd.DataFrame(data, columns=['Match Id', 'Match Number', 'Group Number', 'Team A', 'Team B', 'Innings', 'Over', 'Runs', 'Main Message', 'Complete Commentary'])
df.to_csv('commentary_result_<timestamp>.csv', index=False)
```

### Fetching the Match Page

```
driver.get(url)
```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgements

- [Selenium](https://www.selenium.dev/) - Browser automation
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) - HTML parsing
- [Pandas](https://pandas.pydata.org/) - Data manipulation and analysis

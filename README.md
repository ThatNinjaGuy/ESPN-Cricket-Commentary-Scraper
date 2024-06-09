# Cricket Match Commentary Scraper

## Overview
This project is a web scraping application designed to extract ball-by-ball commentary from a cricket match on the ESPN Cricinfo website. The extracted data is processed and saved into a CSV file for further analysis or usage.

## Features
- **Headless Browsing**: Utilizes Selenium WebDriver in headless mode for faster execution.
- **Efficient Scrolling**: Implements a combination of large and fine scrolling techniques to ensure all content is loaded.
- **Progress Monitoring**: Provides real-time updates on scroll attempts, successful scrolls, and commentary processing progress.
- **Data Extraction**: Extracts detailed commentary information including overs, runs, main messages, and complete commentary.
- **Output**: Saves the extracted data into a CSV file.

## Prerequisites
- Python 3.7 or higher
- Google Chrome browser
- The following Python libraries:
  - `selenium`
  - `bs4` (BeautifulSoup)
  - `pandas`
  - `webdriver_manager`

## Installation
1. **Clone the Repository**
   ```sh
   git clone https://github.com/yourusername/cricket-commentary-scraper.git
   cd cricket-commentary-scraper

Script Details
scraper.py
This is the main script that performs the web scraping and data extraction.

Key Functions
extract_html_content(url):

Sets up the Selenium WebDriver.
Navigates to the specified URL.
Scrolls through the page to load all content.
Captures and saves screenshots at intervals.
Returns the parsed HTML content using BeautifulSoup.
extract_commentary_data(soup):

Extracts commentary data from the parsed HTML.
Prints progress updates for commentary processing.
Returns a list of dictionaries containing the extracted data.
get_processed_data(data):

Converts the extracted data into a Pandas DataFrame.
Saves the DataFrame to a CSV file.
get_urls_to_scrape():

Returns a list of URLs to scrape.
Example Output
After running the script, a CSV file named commentary_results.csv will be generated in the project directory containing the extracted commentary data.

Contributing
Contributions are welcome! Please fork the repository and create a pull request with your changes.

License
This project is licensed under the MIT License. See the LICENSE file for details.

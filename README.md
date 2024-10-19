# Amazon Scraper

This Python script automates the process of scraping product data from Amazon using Selenium and BeautifulSoup. It extracts essential information about products based on a specified search term and outputs the data to a CSV file.

## Features

- **Dynamic URL Generation**: Generates search URLs for Amazon based on user-defined search terms.
- **Data Extraction**: Collects key product details, including:
  - Description
  - Price
  - Rating
  - Review Count
  - URL
- **CSV Output**: Saves the extracted data to a CSV file for easy analysis.

## Requirements

- Python 3.x
- Selenium
- BeautifulSoup4
- Microsoft Edge WebDriver

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/amazon-product-scraper.git
   cd amazon-product-scraper
   ```

2. Install the required packages:
   ```bash
   pip install selenium beautifulsoup4
   ```

3. Download the [Microsoft Edge WebDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) that matches your version of Edge and place it in a directory.

4. Update the path to the Edge WebDriver in the script:
   ```python
   service = Service(r"path_to_your_msedgedriver.exe")
   ```

## Usage

1. Open the script in your preferred Python environment.
2. Adjust the search term in the `main` function:
   ```python
   main("smart watch")
   ```

3. Run the script:
   ```bash
   python amazon_product_scraper.py
   ```

4. The extracted data will be saved to `results.csv` in the same directory.

## Limitations

- The script is currently configured to scrape only one page of search results. You can adjust the range in the `for page in range(1, 2):` loop to scrape more pages.
- Ensure compliance with Amazon's terms of service when using web scraping techniques.

This Python script automates the process of scraping product data from Amazon using Selenium and BeautifulSoup. Here’s a brief overview of its functionality:

URL Generation: The get_url function creates a search URL for Amazon based on the specified search terms, formatting the terms for the URL.

Data Extraction: The extract_record function retrieves relevant details from each product listing, including:

Description
Price
Rating
Review Count
URL
It handles potential missing data by providing default values.

Main Function: The main function orchestrates the scraping:

Initializes the Selenium WebDriver for Edge.
Navigates through the search results for a specified number of pages (currently set to just one).
Uses BeautifulSoup to parse the page source and collect product data.
Compiles the extracted records into a list.
CSV Output: Finally, the script writes the collected product data into a CSV file named "results.csv" for further analysis.

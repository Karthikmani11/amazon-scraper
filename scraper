import csv
from selenium import webdriver
from selenium.webdriver.edge.service import Service
from selenium.webdriver.edge.options import Options
from bs4 import BeautifulSoup

def get_url(search_terms):
    template = "https://www.amazon.com/s?k={}&crid=29WGROR3X4E4G&sprefix=smart+watch%2Caps%2C979&ref=nb_sb_noss_1"
    search_term = search_terms.replace(" ", "+")
    return template.format(search_term)

def extract_record(item):
    atag = item.h2.a
    description = atag.text.strip()
    url = "https://www.amazon.com" + atag.get("href")

    try:
        price_parent = item.find("span", "a-price")
        price = price_parent.find("span", "a-offscreen").text
    except AttributeError:
        price = "Price not found"
    
    try:
        rating = item.i.text
        review_count = item.find("span", {"class": "a-size-base", "dir": "auto"}).text
    except AttributeError:
        rating = "No rating"
        review_count = "No reviews"

    return [description, price, rating, review_count, url]

def main(search_term):
    options = Options()
    options.use_chromium = True

    service = Service(r"C:\Users\gokul karthik\Music\New folder\msedgedriver.exe")
    driver = webdriver.Edge(service=service, options=options)

    records = []
    url = get_url(search_term)

    for page in range(1, 2):
        driver.get(url + f"&page={page}")
        
        # Wait for the page to load (optional but recommended)
        driver.implicitly_wait(10)

        soup = BeautifulSoup(driver.page_source, "html.parser")
        results = soup.find_all("div", {"data-component-type": "s-search-result"})
        
        for item in results:
            record = extract_record(item)
            if record:
                records.append(record)

    driver.quit()

    # Write results to CSV
    with open("results.csv", "w", newline="", encoding="utf-8") as f:
        writer = csv.writer(f)
        writer.writerow(["Description", "Price", "Rating", "Review Count", "URL"])
        writer.writerows(records)

# Run the main function with the search term
main("smart watch")

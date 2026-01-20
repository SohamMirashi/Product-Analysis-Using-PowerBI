# Product-Analysis-Using-PowerBI

This repository contains scripts for web scraping laptop product data from Amazon and Flipkart. The primary goal is to collect detailed product information, such as pricing, ratings, and discounts, and save it into CSV files for subsequent analysis, specifically using Power BI.

## Overview

The project uses Python with `BeautifulSoup` and `requests` to crawl e-commerce sites and extract relevant data. The scripts are designed to gather information on laptops under a specific price point, clean the data, and format it for easy importation into data analysis tools.

## Key Features

*   **Web Scraping:** Extracts data for up to 100 laptops from both Amazon.in and Flipkart.com.
*   **Data Extraction:** Collects the following attributes for each product:
    *   Product Title
    *   Current Price
    *   Original Price
    *   Customer Rating
    *   Number of Reviews
    *   Discount Percentage
*   **Data Cleaning:** The scripts perform basic data cleaning, such as removing currency symbols and commas from price fields and converting them to a numerical format.
*   **CSV Export:** The final, cleaned datasets are saved as `amazon_data.csv` and `flipkart_data.csv`.

## Repository Structure

```
.
├── Amazon_Webscraping.ipynb     # Jupyter Notebook to scrape data from Amazon.
├── Flipkart_Webscraping.ipynb   # Jupyter Notebook to scrape data from Flipkart.
├── amazon_data.csv              # Scraped and cleaned data from Amazon.
├── flipkart_data.csv            # Scraped and cleaned data from Flipkart.
└── README.md                    # This README file.
```

## Methodology

### 1. Web Scraping

The `Amazon_Webscraping.ipynb` and `Flipkart_Webscraping.ipynb` notebooks contain the logic for data collection.

*   The scripts iterate through the search result pages for "laptops under 80000".
*   For each page, they identify and collect individual product page URLs.
*   They then visit each product URL to scrape detailed information using specific HTML tag attributes (classes and IDs).
*   Random delays are implemented between requests to mimic human behavior and avoid being blocked by the servers.

### 2. Data Processing

Once the raw data is scraped, the scripts process it using the `pandas` library:

*   The scraped data is organized into a dictionary and then converted into a DataFrame.
*   Null values are identified and the corresponding rows are dropped to ensure data integrity.
*   Price columns (`current price`, `original price`) are cleaned by removing currency symbols (`₹`) and thousand separators (`,`).
*   The cleaned price columns are converted to a `float` data type for numerical analysis.
*   The processed DataFrames are then exported to their respective CSV files.

## How to Use

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/sohammirashi/Product-Analysis-Using-PowerBI.git
    cd Product-Analysis-Using-PowerBI
    ```

2.  **Install dependencies:**
    Ensure you have Python installed. Then, install the required libraries:
    ```bash
    pip install beautifulsoup4 requests pandas numpy notebook
    ```

3.  **Run the scraping scripts:**
    You can run the Jupyter Notebooks to generate fresh data.
    ```bash
    jupyter notebook Amazon_Webscraping.ipynb
    jupyter notebook Flipkart_Webscraping.ipynb
    ```
    **Note:** Web scraping scripts are dependent on the website's HTML structure. If Amazon or Flipkart updates their site layout, the selectors in the scripts may need to be updated.

4.  **Analyze the Data:**
    Use the generated `amazon_data.csv` and `flipkart_data.csv` files as data sources for your analysis. They can be directly imported into tools like Power BI to build dashboards and visualize product trends.
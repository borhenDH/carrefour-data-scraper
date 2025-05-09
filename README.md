
# Carrefour Tunisia Web Scraper

A robust web scraping tool that extracts detailed product information from Carrefour Tunisia's website, using Selenium and BeautifulSoup to navigate and collect comprehensive product data.

## Features

- **Complete Product Data**: Extracts product images, links, names, prices (current and original), promotions, brands, and descriptions
- **Performance Optimized**: Uses efficient "Load More" button approach instead of page-by-page navigation
- **Robust Error Handling**: Multiple retry mechanisms and graceful failure recovery
- **Progress Tracking**: Saves data incrementally to prevent loss if interrupted
- **Duplicate Prevention**: Ensures products aren't scraped multiple times
- **Browser Management**: Creates fresh browser instances between categories to prevent memory issues
- **Cookie Banner Handling**: Automatically dismisses consent popups
- **Comprehensive Reporting**: Detailed logs and summary statistics

## Requirements

- Python 3.7+
- Chrome browser
- Required Python packages:
  - selenium
  - beautifulsoup4
  - pandas
  - webdriver-manager

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/carrefour-scraper.git
   cd carrefour-scraper
   ```

2. Install required packages:
   ```
   pip install selenium beautifulsoup4 pandas webdriver-manager
   ```

## Usage

1. Run the Jupyter notebook cells in sequence, or run the main script:
   ```
   python carrefour_scraper.py
   ```

2. Data is saved in a `carrefour_data` directory with the following structure:
   - One subfolder per category
   - CSV file with product data in each subfolder
   - progress.json tracking scraping progress
   - summary.json with overview of all categories

## How It Works

1. **Initialization**: Sets up Chrome in headless mode with optimized settings
2. **Category Processing**: Processes each product category URL sequentially
3. **Product Loading**: Uses "Load More" button to reveal all products in a category
4. **Data Extraction**: Parses HTML to extract structured product data
5. **Deduplication**: Checks product links to avoid duplicates
6. **Data Storage**: Saves products to CSV files with regular progress updates

## Code Structure

- **scrape_page()**: Extracts data from a specific page with retry logic
- **extract_products_with_selenium()**: Fallback extraction when BeautifulSoup fails
- **dismiss_cookie_banner()**: Handles cookie consent popups
- **click_load_more_button()**: Efficiently clicks pagination buttons
- **save_progress()**: Stores incremental scraping results
- **scrape_category_with_load_more()**: Main category scraping function
- **main()**: Orchestrates the entire scraping process

## Customization

- **Category URLs**: Edit the `category_urls` list to scrape specific sections
- **Browser Settings**: Modify Chrome options in the setup code
- **Performance**: Adjust wait times and retry attempts to balance speed and reliability

## Troubleshooting

- If scraping fails for specific categories, they'll be marked as "failed" in the summary file
- The scraper will automatically skip completed categories on subsequent runs
- Check the log file for detailed error information
- For specific categories that need re-scraping, use targeted rescraping


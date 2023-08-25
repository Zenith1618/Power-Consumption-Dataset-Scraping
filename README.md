# India Power Consumption Dataset

This repository contains datasets of total power consumption in India for each day from the year 2014 to 2022. Each year's data is stored in a separate dataset. The data is obtained from the [Grid India](https://report.grid-india.in/) website using web scraping techniques and is processed using Python. The workflow for collecting, processing, and storing the data is explained below.

## Workflow

The provided Python script performs the following steps to collect, process, and store the power consumption data:

1. **Date Generation**: The script defines a function `get_valid_dates(year)` that generates a list of valid dates for a given year. This function is used to create a list of dates for the desired year.

2. **Data Collection**:
   - The script sets the target year (e.g., 2022) for which you want to collect the power consumption data.
   - The script obtains a list of valid dates for the specified year using the `get_valid_dates()` function.
   - It uses the `mechanicalsoup` library to interact with the [Grid India](https://report.grid-india.in/) website, input the date, and retrieve the corresponding PDF report link.

3. **PDF Extraction**:
   - The script extracts the PDF link from the webpage and downloads the PDF report for each date using the `requests` library.
   - It then uses the `PyPDF2` library to extract the content from page 2 of the downloaded PDF report and saves it as a new PDF file.

4. **Table Extraction**:
   - The script uses the `tabula` library to read the table data from the PDF file (page 2) and stores it in a pandas DataFrame.
   - The DataFrame is saved as an Excel file named `output.xlsx` using the `openpyxl` engine.

5. **Data Processing**:
   - The script reads the processed Excel file, extracts the relevant data (date and total power consumption), and stores it in a list.

6. **Error Handling**:
   - The script handles exceptions that might occur during data extraction and processing. If an exception occurs, the script appends 'NULL' values to the data list for that date.

7. **Data Storage**:
   - Once all the data is processed, the script creates a new pandas DataFrame from the accumulated data list.
   - The DataFrame can then be saved with any name.

## Instructions

1. Make sure you have Python and the required libraries (`mechanicalsoup`, `requests`, `pandas`, `beautifulsoup4`, `tabula-py`, `PyPDF2`) installed.
2. Modify the `year` variable to the desired year for which you want to collect the data.
3. Run the script to collect, process, and store the power consumption data.

## Disclaimer

Please note that web scraping may be subject to the website's terms of use. Ensure that you are allowed to scrape data from the [Grid India](https://report.grid-india.in/) website for your intended use.

## Note

This script is designed to demonstrate the data collection process and may require adjustments to handle changes on the website or to improve its robustness for long-term usage.

Feel free to contribute and enhance this project for more extensive data collection and analysis.

---


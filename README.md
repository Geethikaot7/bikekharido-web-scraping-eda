# BikeKharido Used Bike Web Scraping & EDA

## Project Overview

This project focuses on collecting used-bike listing data from the **BikeKharido website** and performing data cleaning, exploratory data analysis (EDA), visualization, and business analysis.

The project follows the workflow:

**Website Selection → Data Collection → Data Understanding → Data Cleaning → EDA → Data Visualization → Business Insights → Recommendations**

---

## Project Objective

The main objective of this project is to analyze used-bike listings and understand:

- Used-bike price patterns
- Price differences across locations
- Ownership distribution
- Kilometres driven
- Relationship between kilometres driven and price
- Frequently listed bike models
- Price distribution
- High-priced bike listings
- Business insights from used-bike data

---

## Dataset

The data was collected from the BikeKharido used-bikes webpage.

### Dataset Size

- **Raw scraped records:** 1,200
- **Duplicate records removed:** 602
- **Invalid/missing kilometre record removed:** 1
- **Final cleaned records:** 597
- **Columns:** 5

### Features

| Column | Description |
|---|---|
| `bike_name` | Name/model of the bike |
| `price` | Listed price of the bike in INR |
| `km_driven` | Kilometres driven |
| `ownership` | Ownership category shown in the listing |
| `location` | Location of the bike |

---

## Web Scraping

The data was collected using Python and web-scraping libraries.

### Libraries Used

- Python
- Requests
- BeautifulSoup
- Pandas

### Scraping Process

1. Accessed the BikeKharido used-bikes webpage.
2. Sent HTTP requests using a browser User-Agent.
3. Parsed the webpage using BeautifulSoup.
4. Identified the bike listing cards.
5. Extracted:
   - Bike name
   - Price
   - Kilometres driven
   - Ownership
   - Location
6. Collected listings from multiple pages.
7. Stored the scraped data in a Pandas DataFrame.
8. Saved the raw data as a CSV file.

---

## Data Cleaning

The collected data was cleaned before performing analysis.

### Cleaning Steps

- Checked dataset shape and structure.
- Checked data types.
- Checked missing values.
- Checked duplicate records.
- Removed duplicate rows.
- Removed the `₹` symbol and commas from price values.
- Converted `price` into numeric format.
- Removed `km` from kilometres-driven values.
- Converted `km_driven` into numeric format.
- Checked invalid and unusual values.
- Removed one record where the kilometres-driven value could not be converted into a valid numeric value.
- Checked the cleaned dataset again for missing values and duplicates.

### Final Data Quality

- **Final rows:** 597
- **Columns:** 5
- **Missing values:** 0
- **Duplicate rows:** 0

---

## Exploratory Data Analysis

The following analysis was performed on the cleaned dataset:

### 1. Price Analysis

Analyzed bike prices to understand the overall price distribution and identify high-priced listings.

### 2. Location Analysis

Analyzed the number of bike listings across different locations and compared price patterns between locations.

### 3. Ownership Analysis

Analyzed the distribution of bikes based on ownership categories and compared average price and kilometres driven.

### 4. Kilometres Driven Analysis

Analyzed the distribution of kilometres driven and identified common mileage ranges.

### 5. Price vs Kilometres Driven

Studied the relationship between bike price and kilometres driven to understand how mileage is associated with listed prices.

### 6. Bike Model Analysis

Identified frequently listed bike models and compared average prices across different bike models.

### 7. High-Priced Bike Analysis

Analyzed bikes priced above **₹2,00,000** and identified the locations with more high-priced listings.

### 8. Price Range Analysis

Grouped bikes into different price ranges:

- Under ₹50K
- ₹50K–₹1L
- ₹1L–₹2L
- Above ₹2L

### 9. Kilometre Range Analysis

Grouped bikes into different kilometre ranges:

- Under 10K km
- 10K–25K km
- 25K–50K km
- Above 50K km

---

## Key Findings

- The dataset contains **597 unique used-bike listings** after cleaning.
- Most bikes are listed within the **₹50K–₹2L** price range.
- **First-owner bikes** make up the majority of the listings.
- Major cities such as **Delhi, Mumbai, Bangalore, Pune, and Hyderabad** have a higher number of listings.
- Most bikes fall within the **10K–50K km** range.
- Higher kilometres driven generally show a **negative relationship with listed price** in the analyzed dataset.
- The dataset contains a mix of regular used bikes and higher-priced premium bikes.
- Some listings have unusually high prices compared with the majority of the dataset and were reviewed separately during analysis.

---

## Business Insights

The analysis shows that used-bike prices can vary based on multiple factors such as:

- Bike model
- Kilometres driven
- Ownership
- Location

Looking at these factors together gives a better understanding of used-bike pricing and inventory patterns.

The analysis can help a used-bike marketplace understand its inventory, pricing patterns, location-wise listings, and different customer-focused bike categories.

---

## Business Recommendations

- Provide filters for **price, kilometres driven, ownership, and location**.
- Create categories such as **Budget Bikes, Mid-Range Bikes, and Premium Bikes**.
- Highlight bikes with lower kilometres driven.
- Clearly display ownership information for each listing.
- Monitor pricing differences across major locations.
- Review unusually high-priced listings separately before using them for normal price comparisons.
- Continue collecting more listings from different pages and locations for broader analysis.
- Use bike model, mileage, ownership, and location together when comparing prices.

---

## Visualizations

The project includes visualizations for:

- Bike price distribution
- Listings by location
- Average price by ownership
- Average kilometres by ownership
- Top bike models by listing count
- Top bike models by average price
- High-priced bikes by location
- Price range distribution
- Kilometre range distribution
- Price vs kilometres driven

---

## Tools & Technologies

- **Python**
- **Requests**
- **BeautifulSoup**
- **Pandas**
- **Matplotlib**
- **Jupyter Notebook**
- **CSV**

---

## Project Structure

```text
bikekharido-used-bike-analysis/
│
├── 01_scraped_data.ipynb
├── 02_data_cleaning.ipynb
├── 03_eda_analysis.ipynb
│
├── bikekharido_used_bikes_collected.csv
├── bikekharido_used_bikes_cleaned.csv
│
└── README.md
---

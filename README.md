# BikeKharido Used Bike Web Scraping & EDA

## Project Overview

This project focuses on collecting used-bike listing data from the
BikeKharido website and performing data cleaning, exploratory data
analysis (EDA), visualization, and business analysis.

The project follows the workflow:

**Website Selection → Data Collection → Data Understanding → Data
Cleaning → EDA → Data Visualization → Business Insights →
Recommendations**

## Project Objective

The main objective is to analyze used-bike listings and understand:

-   Used-bike price variation
-   Price differences across locations
-   Ownership distribution
-   Relationship between kilometres driven and price
-   Highest- and lowest-priced bikes
-   High-mileage bikes
-   Factors that can help understand used-bike pricing and inventory

## Dataset

The final analysis contains **11 valid unique used-bike listings**
collected from the BikeKharido used-bikes page.

### Features

  -----------------------------------------------------------------------
  Column                              Description
  ----------------------------------- -----------------------------------
  `bike_name`                         Name/model of the bike

  `price`                             Seller-demand price of the bike in
                                      INR

  `km_driven`                         Kilometres driven

  `ownership`                         Number of previous owners/category
                                      shown in the listing

  `location`                          City/location of the bike
  -----------------------------------------------------------------------

Two datasets are maintained:

-   `bikekharido_used_bikes_collected.csv` --- raw collected data
-   `bikekharido_used_bikes_cleaned.csv` --- cleaned data used for
    analysis

## Web Scraping Process

The data was collected from the BikeKharido used-bikes webpage using
Python.

### Libraries Used

-   `requests`
-   `BeautifulSoup`
-   `pandas`

### Scraping Steps

1.  Sent an HTTP request to the BikeKharido used-bikes webpage.
2.  Used a browser User-Agent in the request headers.
3.  Parsed the HTML using BeautifulSoup.
4.  Identified the bike listing cards from the webpage.
5.  Extracted:
    -   Bike name
    -   Seller-demand price
    -   Kilometres driven
    -   Ownership
    -   Location
6.  Stored the extracted records in a Pandas DataFrame.
7.  Saved the collected data as a CSV file.

## Data Cleaning

The collected data was checked and cleaned before analysis.

### Cleaning Steps

-   Checked dataset structure and data types.
-   Checked for missing values.
-   Checked for duplicate records.
-   Removed duplicate rows.
-   Removed the `₹` symbol and commas from the price values.
-   Converted `price` from text to numeric format.
-   Removed `km` from the kilometres-driven values.
-   Converted `km_driven` to numeric format.
-   Checked for unrealistic/outlier values.
-   One `Magnus EX` listing contained an invalid source price of
    `₹9,27,01,01,577`. The original webpage was checked and showed the
    same value, so the record was excluded rather than replacing the
    source value with an invented price.
-   Removed the unnecessary index column from the cleaned dataset.

## Exploratory Data Analysis

The following analyses were performed:

### 1. Price Distribution

The valid listings have prices ranging from **₹15,000 to ₹95,000**.

### 2. Listings by Location

-   Mumbai --- 3 listings
-   Kolkata --- 3 listings
-   Jaipur --- 1 listing
-   Hyderabad --- 1 listing
-   Indore --- 1 listing
-   Pune --- 1 listing
-   Delhi --- 1 listing

### 3. Average Price by Location

  Location      Average Price
  ----------- ---------------
  Mumbai              ₹70,000
  Kolkata             ₹40,000
  Indore              ₹36,000
  Delhi               ₹35,000
  Jaipur              ₹34,000
  Pune                ₹25,000
  Hyderabad           ₹16,000

The location-level results should be interpreted cautiously because most
locations contain only one listing.

### 4. Ownership Distribution

-   First owner --- 9 listings
-   Second owner --- 1 listing
-   Third owner --- 1 listing

### 5. Average Price by Ownership

-   First owner --- approximately ₹38,556
-   Second owner --- ₹95,000
-   Third owner --- ₹34,000

The second- and third-owner averages are based on only one listing each.

### 6. KM Driven vs Price

The correlation between kilometres driven and price is approximately
**-0.67**, indicating a moderate negative relationship in this sample.

This means that bikes with higher kilometres driven generally tend to
have lower listed prices in the analyzed data. Correlation does not
establish causation.

### 7. Highest-Priced Bikes

  Bike                                 Price
  -------------------------------- ---------
  XPulse 200 4V                      ₹95,000
  Shine Celebration Edition Drum     ₹90,000
  S1 X                               ₹75,000
  Avenger Cruise 220 BS6             ₹36,000
  Victor                             ₹35,000

### 8. Lowest-Priced Bikes

  Bike                     Price
  -------------------- ---------
  Dio Repsol Edition     ₹15,000
  Karizma R              ₹16,000
  Activa 3G STD          ₹25,000
  Dio BS4 Dio            ₹25,000
  Drift                  ₹30,000

### 9. Highest-Mileage Bikes

  Bike                                            KM Driven
  -------------------------------------------- ------------
  Karizma R                                      100,000 km
  Dio Repsol Edition                              90,000 km
  Dio BS4 Dio                                     70,000 km
  Activa 3G STD                                   60,000 km
  Maestro Edge 110 Drum Brake Alloy Wheel FI      28,000 km

## Key Business Insights

1.  Used-bike prices show considerable variation, ranging from **₹15,000
    to ₹95,000** in the cleaned dataset.
2.  Mumbai has the highest average listed price at **₹70,000** among the
    locations analyzed.
3.  Mumbai and Kolkata have the highest number of listings in this
    sample, with **3 listings each**.
4.  First-owner bikes dominate the dataset, accounting for **9 of the 11
    valid listings**.
5.  KM driven has a moderate negative correlation with price (**-0.67**)
    in this sample.
6.  XPulse 200 4V has the highest listed price at **₹95,000**.
7.  Dio Repsol Edition has the lowest listed price at **₹15,000**.
8.  The highest-mileage bikes are generally among the lower-priced
    listings.
9.  Data validation is important because one source listing contained an
    obviously invalid price value.

## Business Recommendations

1.  **Consider mileage when evaluating prices:** Kilometres driven can
    be included as one factor when comparing or pricing used bikes.
2.  **Monitor location-level pricing:** Locations with more listings,
    such as Mumbai and Kolkata in this sample, can be monitored for
    changes in listing prices and inventory.
3.  **Use price segmentation:** Listings can be grouped into budget,
    mid-range, and higher-price categories to make comparisons easier.
4.  **Highlight lower-mileage bikes:** Lower-mileage vehicles can be
    emphasized when presenting options to customers.
5.  **Display ownership information clearly:** Ownership history should
    be visible so customers can compare listings more effectively.
6.  **Validate scraped data:** Automated scraping results should be
    checked for missing, duplicate, and unrealistic values before
    analysis.
7.  **Expand the dataset:** More listings, pages, cities, and bike
    models should be collected to obtain broader and more reliable
    market-level insights.

## Project Limitations

-   The analysis is based on **11 valid unique listings** from the
    scraped dataset.
-   The sample is not large enough to represent the entire used-bike
    market.
-   Several locations and ownership categories contain only one listing.
-   The analysis describes relationships in the collected sample and
    does not establish causation.

## Tools & Technologies

-   Python
-   Requests
-   BeautifulSoup
-   Pandas
-   Matplotlib
-   Jupyter Notebook
-   CSV

## Project Structure

``` text
bikekharido-web-scraping-eda/
│
├── 01_scraped_data.ipynb
├── 02_data_cleaning.ipynb
├── 03_eda_analysis.ipynb
│
├── bikekharido_used_bikes_collected.csv
├── bikekharido_used_bikes_cleaned.csv
│
└── README.md
```

## Conclusion

This project demonstrates a complete beginner-friendly web-scraping and
EDA workflow using used-bike listings. The analysis identifies patterns
in pricing, location, ownership, and kilometres driven while also
demonstrating the importance of data cleaning and validation before
drawing business insights.

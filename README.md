# Apartment Hunting on Craigslist
## Using linear regression to predict rental prices in San Francisco

:construction: an introduction goes here :construction:

### Data Scraping and Cleaning
* Scraped +3,000 apartment/housing posts on [Craigslist](https://sfbay.craigslist.org/) (including listings results pages and individual posts)
    * [Data scrape date: Oct 1, 2020 - 6:50pm](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/craigslist_scrape_sf.ipynb)
    * Listings date range: Sept 30 - Oct 1, 2020
* After removing duplicates and rows with missing key values, 1,000 unique listings remained. The raw scraped data and cleaned data can be found in the [data_files](https://github.com/scrapfishies/CL-housing-rent-predictions/tree/master/data_files) folder. 

![Anatomy of a Craigslist Post](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/img/post_example.png?raw=true)

### Features and Target Variable
* **Target varible: *monthly rental price***
* Features
  * unit size (sqft)
  * number of bedrooms
  * number of bathrooms
  * location (per the [SF Realtor Association district map](https://data.sfgov.org/Geographic-Locations-and-Boundaries/Realtor-Neighborhoods/5gzd-g9ns))   
  * amenities (parking situation, pets allowed, laundry facilities)  

### Model Results and Evaluation
Overal, the model does a reasonable job of predicting apartment rental prices based on these standardized listing features. The ~$400 price variation should be considered in relation to the apartment price, and an apartment hunter's tolerance will be subjective to their budget. For example, this swing could be substantial for one person's budget, but may be okay when splitting between multiple people. 

The model does best when predicting prices for units in the $2,500 to $4,000 / month range, which represents the majority of listings in the sample.

![Predicted versus Actual](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/img/ridge_actual_predicted.png?raw=true)

There are most certainly other factors influencing rent. For example, many apartments in San Francisco are subject to rent control, which can impact a new listing's price. There may also be other amenities offered that aren't standard fields in Craigslist (e.g. fitness facilities, common spaces). Lastly, there may be other environmental or economic factors at play -- San Francisco is currently seeing an unprecedented drop in rental prices as many people have left the city during COVID. The sample may not be a typical representation of available housing compared to pre-pandemic times, as those vacancies may be attributed to former residents who have the means to move out of the city and work remotely. 

* Model Scoring Metrics
  * R-squared: 77%
  * Root Mean Squared Error (RMSE): ~$475
  * Mean Absolute Error (MAE): ~$365
* [Presentation deck](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/predicting_apt_rentals_in_sf.pdf)
* [Exploratory Data Analysis Charts](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/eda_charts.ipynb)
* [Linear Regression Model Notebook](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/linear_regression_model.ipynb)
  
### Suggestsion for Future Work
* Sample again when COVID's impact subsides
* Increase features with more advanced scraping and data processing methods
  * search post text for keywords like 'gym' or 'backyard' for additional amenities
  * find information on security deposit and/or lease requirements
  * implement image processing tools to evaluate an apartment's quality from the post's photos
* Scam post identification  

#### Tooling
* General
  * `Python`, `Jupyter Notebooks`
  * `Pandas`
  * `Numpy`
* [Web scraping](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/scrape_cl.py)
  * `requests`
  * `BeautifulSoup`
* [Modeling](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/linear_regression_model.ipynb)
  * `sklearn`
  * `statsmodels`
* [Visualizations](https://github.com/scrapfishies/CL-housing-rent-predictions/blob/master/eda_charts.ipynb)
  * `Seaborn`
  * `Matplotlib`

#### Sources & References: 
* [San Francisco Association of Realtors](https://my.sfrealtors.com/)
* [Data SF](https://data.sfgov.org/Geographic-Locations-and-Boundaries/Realtor-Neighborhoods/5gzd-g9ns) for neighborhood-district mapping
* [SF Chronicle: Bay Area rents keep plumetting... (10/02/2020](https://www.sfchronicle.com/bayarea/article/Bay-Area-rents-keep-plummeting-especially-in-15613722.php)
* [Medium: Web Scraping Craigslist](https://towardsdatascience.com/web-scraping-craigslist-a-complete-tutorial-c41cea4f4981)



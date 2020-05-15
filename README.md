# Project 5 - Client
Khadija Conteh, Matt DeVay, Aidan Dominguez

---

#### Problem Statement:
Create a feature that could enhance current image-based predictions of informal settlements based on the ratio of real estate adverts to population density.

Informal Settlements: Unplanned areas where housing is constructed on land that occupands have no legal clai to or occupy illegally 
(source: Glossary of Environment Statistics, Studies in Methods, Series F, No. 67, United Nations, New York, 1997.)

---

Workflow: 
1. Research
2. Collect Real Estate Data via webscraping
3. Geocode Real Estate Data
4. Regionalize Population Density Data
5. Correlate Real Estate Data to population for each region

---
#### City: Nairobi

City Background: 
- Modern, rapidly growing city
- Large and dynamic informal settlements
- Accurate and recent population data available

---

#### Process

We began by getting <a href=https://data.humdata.org/>Population Density Data for Kenya</a> with over 11 million data points. From there, we narrowed the data to a grid arond Nairobi, which brought the data to about 400,000 data points. 

Next, we scraped renting and buying advertisements from <a href=https://www.buyrentkenya.com>buyrentkenya.com</a>. We wrote all of the advertisement data to a csv.

We then geocoded the specific location data for all advertisements using Google Maps API based off the little location information that was scraped from the real estate site. Specific longitutde and latitude data was appended to the real estate advert csv for analysis.

Analysis began by dividing advert data by county and sub-county, and looking at property prices and rental prices to have an idea of where the affluent neighborhood were located. We then continued by comparing real estate data with primary school locations and water/sewage locations to get a better idea graphically of where these informal settlements might appear.

For modeling, population data was initially filtered in 5 different ways based off population size: population greater than 2, greater than 4, greater than 5, greater than 6, greater than 7, and greater than 8. The data for each was scaled and modeled using a K-Means model, manually grid searched for k values ranging from 1 to 40. After assessing each model, the best model used a k of 27 with a silhouette score of 0.54. The model was fit on the scaled data, and used to classify advert and population data points using latitude and longitude.

Using the model, advert data was assigned a cluster using latitude and longitude. This cluster information was then used to create a ratio for each cluster using amount of adverts per cluster and average population per cluster.

---

#### Challenges
- Selecting site to scrape
- Lack of data reference for advertisements
- Generalized or missing advert locations
- Misclassification of advert locations
- Price currency conversion

---

Technology Used:
- Python (sklearn, matplotlib, pandas)
- Selenium
- QGIS
- Google Earth Pro
- Google Maps
- Google Maps API
- Tableau

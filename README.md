# How can we predict house price from its features?  
## Introduction  
Real estate is a lucrative business that has attracted great investments in recent times. In order to be competitive in business, real estate agents needs to be able to value a house easily and appropriately before they can invest in such property. The business question that I seek to answer is: How can real estate agents predict house price from a number of house features such that the house is not under-valued or over-valued. This is critical, as agents want to avoid under-valuation to maximize profit and also avoid over-valuation to prevent the property from staying too long in the market.
 To address this, house prices including their features were scraped from zoopla website, a popular property letting and sale website in the England. The data were scrapped in json format and then converted to csv format to be used for this project.
### Data collection  
The house price data was scrapped from zoopla website.
**Data Information**  
Number of records: 36213  
Number of columns: 20  
Features:  
* Agent_name – Name of the agent in charge of the property  
* Condition-  Whether the house is new or pre-owned.  
* Distance_to_charing_cross: Distance between the property and Charing Cross station.    
* Distance_to_closest_airport: Distance between the property and the nearest airport.    
* Distance_to_closest_dlr_or_underground_station  : Distance between the property and the closest DLR or underground train station.  
* Distance_to_closest_national_rail_station:    Distance between the property and the closest national rail train station.         
* Distance_to_closest_primary_school: Distance to the closest primary school.   
* Latitude: Latitude of the location of the property.  
* Longitude: Longitude of the location of the property.   
* n_bathrooms:  Number of bathrooms in the property.  
* n_bedrooms: Number of bedrooms in the property.  
* n_reception_rooms: Number of  reception rooms in the property.  
* Postcode: The postcode of the property that shows the region the property is located within London.  
* Price_qualifier : Description of the price. For example, ‘from £250,000’, ‘offer over  £250,000’ and so on.  
* Property_type: The type of the property. For example flat, mews, detached and so on.  
* Size_sqft:  The size of the house in square foot.  
* Status: The status of the house. For example, ‘for sale’, ‘sold’, ‘sale under offer’ and so on.  
 * Tenure: The tenure type. For example, ‘leasehold’, ‘freehold’ and so on.   
 * Price: The price of the house to be predicted. 
### Preprocessing  
The features were categorized into numerical, categorical numerical and categorical features. Features with text values are categorical while numeric features with less than 13 unique values were categorized as categorical numerical.   
**Data cleaning**  
The data has some missing values. Two categorical features, ‘price_qualifier’ and ‘tenure’ contain 79% and 40% missing values respectively and were replaced with the word ‘missing’. 
The categorical numerical features all have missing values. The n_bathrooms, n_bedrooms and n_reception_rooms features have 12%, 4% and 20% missing values respectively and were filled with the mode of the respective feature. 
For numerical features,  distance_to_closest_dlr_or_underground_station,  distance_to_closest_national_rail_station and size_sqft have 7%, 4% and 82% missing values respectively.  Since most of the records are missing in size_sqft, this feature was dropped. The remaining two features were filled with the mode of the respective feature.
### Exploratory Data Analysis
The exploration of the relationship between target and features as well as the relationship between features revealed the following:  
* Pre-owned houses are cheaper than new homes based on the mean price across all properties.  
* Detached houses seem to be the most expensive based on the mean price. However, no conclusion can be made now as the house price needs to be explored based on the number of rooms as well.  
* Houses with label 'sold' tends to have lower price compared to 'under offer' and 'for sale' ones.  
* Mews houses with 1-5 bedrooms tend to be the most expensive. This is probably because of great benefits including quiet area, access to good parking area, friendly community and security.  
* For houses with more than 5 bedrooms, the highest mean price tends to vary with the number of bedrooms. This implies that other factors are at play in determining the highest price.  
* Only two types of properties have 12 bedrooms (flat and semi-detached).  
### Correlation with target
Some of the features are positively correlated with house price. These include n_bathrooms, n_bedrooms, n_reception_rooms , distance_to_closest_airport and size_sqft. Distance_to_charing_cross station and longitude are negatively correlated with the target. The negative correlation of distance_to_charing_cross the target with seems to be surprising as Charing cross station is a famous station in Central London. However, this is what the data shows. Other features are weakly correlated with the target.  
### Feature Engineering  
The postcode feature was binned into groups based on the area/district code. This reduces the number of unique values in the postcode variable from 18000 to 100.
### Modeling
Features with lots of missing records and those that may not contribute to the house price prediction were dropped. These features are ‘id’, ‘status’ , size_sqft and ‘price_qualifier’. ‘status’ was dropped because it contains three labels with one of the labels having 99.9% of the total count. ‘size_sqft’ and ‘price_qualifier’ were dropped because they both have over 78% missing values.
One-hot-encoding was used to transform the categorical features into numerical for modeling.  
80% - 20% train-test split was used
Models:  
Machine learning models including linear regression, Random forest regressor, Gradient boosting regressor, XGBoost and LightGBM were used to model the data with LightGBM coming out as the best based on MSE. The results are summarized in the table below:



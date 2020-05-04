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


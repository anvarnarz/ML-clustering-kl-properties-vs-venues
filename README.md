# Kuala Lumpur Neighborhood Analysis using Machine Learning Clustering algorithm
In this project we will compare different neighborhoods of Kuala Lumpur based on Real estate dataset (property prices, types, sizes) and venues around the neighborhood.

# Introduction

Kuala Lumpur, the capital of Malaysia is a home to about over 7 million people and is split into more than 40 districts. Each neighborhood has its own features and characteristics. Some are popular for parks and tourist attractions, while others are dense urban neighborhoods with office buildings and skyscrapers. There are neighborhoods mostly populated with local Chinese people, and places with large expat community.
There are industrial neighborhoods with houses for low income foreign labour, and areas such as Damansara Heights, the home of celebrities, politicians and rich people in general.

In this project we will compare different neighborhoods of the KL city based on property prices, types and venues around that neighborhood using machine learning clustering algorithms.

# Business Problem

There are many reasons people relocate within city boundaries, e.g. getting a new job offer, kids moving to different school or moving away from bad neighborhood etc. This project will help such people to compare different neughborhoods of Kuala Lumpur city in terms of property types, prices, size and most importantly the venues around specific neighborhood. If you're looking for a better neighborhood with more parks or coffee shops and restaurants but with similar real estate price, this is the place for you.

# Dataset
We will use the [dataset](https://www.kaggle.com/dragonduck/property-listing-analysis) created by Jan S available on [Kaggle](https://www.kaggle.com).
This dataset contains tens of thousands of property listings scraped from iproperty.com for every neighborhood of Kuala Lumpur city.
The dataset contains such information as number of rooms, bathrooms, parking slots, furnshing condition, property type and size as well as price per room and price per area for each listed property in iproperty.com.

![Real estate dataset KL](images/figure1.png)
For venues around each neighborhood we will gather data from Foursquare.com.

# Methodology
We will divide the project into multiple phases:

<b>Step 1 is Data wrangling.</b> Real estate dataset has many missing values, i.e. some properties missing the number of rooms info, others does not have the furnishing or size data. Rather than filling missing values we will simple remove the raws with NaN values, and still have a huge dataset with over 31000 property listings.

<b>Step 2 is Getting Latitude and Longitude coordinates for each  neighborhood.</b> We will use Geopy geocoders library to do so.

![](/images/figure2.png)

<b>Step 3 is Data analysis and clustering based on real estate data.</b> We will use onehot encoding to convert categorical data such as type of property and furnishing condition into numericla form. Next we will perform the K-means clustering algorithm. After few experiments we decided to set K=5.

![](/images/figure2a.png)

<b>Step 4 is collecting data about each neighborhood using a Foursquare API.
  
![](/images/figure3.png)

We will collect 100 venues around each neighborhood based on longitude and latitude information.

![](/images/figure3a.png)

Next we will select top 10 venue for each neighborhood and perform a onehot encoding.

![](/images/figure3b.png)

<b>Step 5 is Clustering based on Neighborhood venues.</b> 
In this we will perform the K-means clustering algorithm using venues dataset. We will use the same number of clusters as before (real estate clustering). 

<b>Step 6 is comparing both clustering results,</b> 
and see how different neighborhoods correlated in terms of real estate dataset as well as venues around them. 

# Results
## Real estate based clustering 

Lets analyse clustering results based on Real estate dataset:

![](/images/figure4.png)

We have 5 clusters. Let's analyse each cluster one by one.

<b>Cluster 0 (red circles)</b> is characterized by expensive properties with area size from 1500 to 4000 sqft. Most of the properties in this cluster are serviced residences and condominiums.  The price in this cluster is rather high, with price per room from RM400K all the way up to RM700K. The neighborhoods in this cluster are mostly located close to KL downtown, such as KLCC, Bukit Bintang, KL central, Seputeh.

![](/images/figure5.png)

<b>Cluster 1 (purple circle)</b> has only a single member: 
<b>Country Heights Damansara</b>. 
This is a luxury neighborhood with luxury villas (over 80% properties here are bungalows/villas). This is the home of celebrities, politicians and rich people in general. Properties in this area are rather huge with over 9000 sqft in average, 5 parking spots, and skyrocket prices (over RM1.5 million per room). 

![](/images/figure6.png)

<b>Cluster 2 (light blue circles)</b> 
is the biggest cluster that includes the neighborhoods with properties for low to middle income families. These neighborhoods are scattered all around the city. The properties in this cluster are anywhere from 900 to 2000 sqft in size and the price per room vary from RM100K to RM400K. 

![](/images/figure7.png)

<b>Cluster 3 (light green circles)</b> 
includes 2 expensive neighborhoods with large properties (over 5000 sqft) and high price values (over RM900K per room). 

![](/images/figure8.png)

<b>Cluster 4 (yellow circles)</b> 
includes three neighborhoods for upper income category. Most of the properties here are condominiums and serviced residences, with average size of over 3000 sqft. Price per room in this cluster is around RM700K in average. 

![](/images/figure9.png)

## Venues based clustering

Next we cluster the neighborhhods based on Venues dataset obtained from Foursquare.com.

First, lets look at the top 10 venues for different neighborhoods:

![](/images/figure10.png)

Let's see the clustering results. 

![](/images/figure10a.png)

<b>Cluster 0 (red circle)</b>
Consists of single neighborhood (Segambut) and distinc character of this area is lack of restaurants in top 10 venues.

![](/images/figure10b.png)

<b>Cluster 1 (purple circles)</b> 
Includes tourist hotspots and crowded areas. These are very diverse neighborhoods with a lot of Cafes, Restaurants, Coffee shops, Department stores, Shopping malls, entertainment centers etc. 

![](/images/figure10c.png)

<b>Cluster 2 (blue circles)</b>
is mostly residential areas characterised by a lot of eatiries, food trucks, food courts and coffee shops. 

![](/images/figure10d.png)

<b>Clusters 3 and 4 (green and yellow circles, respectively)</b>
are rich people neighborhoods with Art Gallery, Yoga studios, Pool and hiking trail. 

![](/images/figure10e.png)

## Real-estate vs Venues

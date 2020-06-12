# Kuala Lumpur Neighborhood Analysis using Machine Learning Clustering algorithm
In this project we will compare different neighborhoods of Kuala Lumpur based on Real estate prices, types, sizes and venues around the neighborhood.

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

<b>Step 3 is Data analysis and clustering based on real estate data.</b> We will use onehot encoding to convert categorical data such as type of property and furnishing condition into numericla form. Next we will perform the K-means clustering algorithm.

![](/images/figure2a.png)

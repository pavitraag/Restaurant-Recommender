# Restaurant-Recommender

The directory contains web sub directories and a sub directory for hosting model and other scripts:

1.app.py The file which contains all the main backend operations of the website and used to run the flask server locally.

2.requirement.txt contains all the dependencies.

3.templates contains the html file.

|- - - home.html contains home page.

|- - - search.html contains search page.

4.static contains the css file and images.

|- - - home.css contains Styling of home page.

|- - - search.css contains Styling of Search page/ result page.

|- - - backgrund1.jpg contains background image of web pages.

5.main_rest.csv contains the raw data.

6.food1.csv contains cleaned data.

**Dependencies**

The following dependencies can be found in requirements.txt:

-scikit-learn

-Flask

-pandas

-numpy

-scikit-learn

-gunicorn

**Explanation**

This code appears to be a Python script for a Flask web application that provides restaurant recommendations based on user input. Let's break down the code step by step:

-**Importing Libraries:**

The code starts by importing several libraries required for the application. These include Flask for creating the web application, pandas for data manipulation, scikit-learn for machine learning, and other related libraries.

-**Data Preparation:**

A dataset of restaurants is loaded from a CSV file named "food1.csv" using pandas.
Label encoding is applied to two columns, 'cuisines' and 'locality', to convert categorical data into numerical format.
Min-Max scaling is applied to the 'average_cost_for_one' column to normalize its values.
A k-nearest neighbors (KNN) model is trained on the dataset using the 'cuisine_encoded', 'average_cost_for_one', and 'locality_encoded' features. This model is used for recommending restaurants.

-**Function Definitions:**

--fav(lko_rest1): This function takes a DataFrame as input and performs content-based filtering for restaurant recommendations based on restaurant highlights. It returns a DataFrame containing recommended restaurants.

--rest_rec(cost, people=2, min_cost=0, cuisine=[], Locality=[], fav_rest="", lko_rest=lko_rest): This function takes user preferences (budget, number of people, cuisine, locality, and a favorite restaurant) and filters the dataset to recommend restaurants that match these preferences. It returns a DataFrame with restaurant recommendations.

--calc(max_Price, people, min_Price, cuisine, locality): This function calls rest_rec to get restaurant recommendations and prepares the recommendations in a suitable format for displaying on the web page.

-**Flask Application:**

A Flask web application is created with the name "app".

Restaurant data is loaded from the "food1.csv" file.

The /search route handles the restaurant search functionality.

It retrieves user input for the number of people, minimum price, maximum price, cuisine, and locality.

It calls the calc function to generate restaurant recommendations based on user input.

The recommendations are then passed to the "search.html" template for rendering.

-**Main Block:**

The main block at the end of the code checks if the script is being run directly and starts the Flask web application with debugging enabled.

In summary, this code sets up a Flask web application for restaurant recommendations. It uses a combination of content-based and K-nearest neighbors recommendation approaches to suggest restaurants based on user preferences such as budget, cuisine, and locality. The recommendations are then displayed to the user through a web interface.

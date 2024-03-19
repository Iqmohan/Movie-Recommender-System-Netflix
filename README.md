# RECOMMENDER-SYSTEM
This Project is on Singular Value Decomposition (SVD) Algorithm  which estimated the user's approach and latent factors and provide the estimated score based on which the movie or the content is recommended.
Netflix Analytics - Movie Recommendation.

This project aims to build a movie recommendation mechanism within Netflix. The dataset consists of 4 text data files, each file has a shape (24058263, 2) rows & columns, i.e. over 4499 movies and 475257 customers. All together over 17K movies and 500K+ customers!
One of the major challenges is to get all these data loaded into the Kernel for analysis, I have encountered many times of Kernel running out of memory and tried many different ways of how to do it more efficiently.
Objective
Learn from data and recommend best TV shows to users, based on self & others behaviour.

Data manipulation

Data loading

Data viewing

Data cleaning

Data slicing

Data mapping

Recommendation models

Recommend with Collaborative Filtering using SVD algorithm

Data manipulation
step 1 - Data loading Each data file (there are 4 of them) contains below columns:

Movie ID (as first line of each new movie record / file)

Customer ID

Rating (1 to 5)

Date they gave the ratings.

There is another file contains the mapping of Movie ID to the movie background like name, year of release, etc

Let's import the library we needed before we get started:

Netflix prize dataset importing the necessary libraries for importing the dataset in jupyter notebook Around 100M+ ratings 4499 movies 480,000+ users

step 2 - mount drive link to the notebook which has dataset in it using import drive (colab)

step 3 - Reading dataset file

step 4 - extracting the bottom 5 rows using (netflix_dataset.tail())

step 5 - chechking the data types of each column

step 6 - Get the customer count with NaN values

step 7 - To calculate how many customers we are having in the dataset

step 8 - Extracting the number of times ratings given

step 9 - Get the total number of ratings given by the customers.

STEP 10 - To find out how many people have rated the movies as 1, 2, 3,4,5 stars ratings to the movies

      # 1st method using value_counts()
step 11 -To find out how many people have rated the movies as 1, 2, 3,4,5 stars ratings to the movies

    # 2nd method netflix_dataset.groupby('Rating')['Rating'].count().
step 12 - To find out how many people have rated the movies as 1, 2, 3,4,5 stars ratings to the movies

            # 3rd method
        stars=netflix_dataset.groupby('Rating')['Rating'].agg(['count'])
step 13 - Plotting the total movies,cutomers and ratings given..

step 14 - Add another column that will have movie id

step 15 - To reset the index as the column

step 16 - To extract all the records from the index column except for the last index-- 4498

step 17 - df_nan['index'][1:] This sytax will extract records from the index column from the 1st index

step 18 - full function

step 19 - taking tuple

step 20 - create a numpy array that will contain 1 from values 0 to 547, 2 from 548 to 693 and so on...

step 21 - extrating the transformed dataset.

step 22 - To remove all the users that have rated less movies and also all those movies that has been rated less in numbers

step 23 - dataset_movie_summary

step 24 - Applying Benchmark to take 70 % of data from above

step 26 - To remove all the customers and movies that are below the benchmark

step 27 - importing Pandas Library to impory movie titles dataset

step 28 - model building

import math import seaborn as sns from surprise import Reader, Dataset, SVD from surprise.model_selection import cross_validate

step 29 - help us to read the dataset for svd algo reader=Reader()

step 30 - we only work with top 100K rows for quick runtime

step 31 - creating object model=SVD()

step 32 - cross_validate(model, data, measures=['RMSE','MAE'], cv=4)#cv=4: This parameter specifies the number of folds for cross-validation. In this case, it's set to 4, meaning the dataset will be split into 4 parts, and the model will be trained and evaluated four times, each time using a different fold as the test set.

step 33 - the output you provided appears to be the result of running collaborative filtering model evaluation using cross-validation. Let's break down each part:

'test_rmse': This is an array of Root Mean Squared Error (RMSE) values for each fold during cross-validation. RMSE is a common evaluation metric for collaborative filtering models, measuring the average prediction error.

'test_mae': This is an array of Mean Absolute Error (MAE) values for each fold during cross-validation. MAE is another common evaluation metric, representing the average absolute difference between predicted and actual ratings.

'fit_time': This is a tuple containing the time taken to fit (train) the model for each fold during cross-validation. It provides insights into the training time for each iteration.

'test_time': This is a tuple containing the time taken to evaluate the model on the test set for each fold during cross-validation. It gives information about the time it takes make predictions on unseen data.

Putting it all together, here's a summary:
RMSE and MAE: These metrics provide an indication of how well the collaborative filtering model is performing on predicting user ratings. Lower values for both RMSE and MAE are generally better, indicating better accuracy.

fit_time: This shows the time it took to train the model for each fold. It's essential to monitor, especially if you're working with large datasets or complex models. Longer fit times might impact the model's scalability.

test_time: This shows the time it took to make predictions on the test set for each fold. Similar to fit time, test time is important for assessing the model's efficiency during inference on new data.

In summary, the provided output is a comprehensive summary of the collaborative filtering model's performance during cross-validation, covering accuracy metrics (RMSE, MAE) and computational aspects (fit time, test time). Lower RMSE and MAE values, along with reasonable fit and test times, generally indicate a well-performing and efficient collaborative filtering model.
step 34 -so first we take user 1331154 and we try to recommend some movies based on the past data,he rated so many movies with 5 .

step 35 - #now we will build the recommendation algorithm #first we will make a shallow copy of the movie_titles.csv file so that we can change #the values in the copied dataset, not in the actual dataset

user_1331154=df_title.copy() user_1331154

step 36 - Getting Estimate_Score in descending orderScreenshot (1980)Screenshot (1979)Screenshot (1977)Screenshot (1976)

END OF THE PROJECT

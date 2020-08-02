# Log Mining
**Data**:
the [NASA access log July 1995 data](ftp://ita.ee.lbl.gov/traces/NASA_access_log_Jul95.gz).
Please read the *[dataset description](ftp://ita.ee.lbl.gov/html/contrib/NASA-HTTP.html)* to understand the data and complete the following four tasks.


A. Find out the **average number** of requests on each four hours of a day of July 1995 by the local time (i.e. 00:00:00-03:59:59; 04:00:00-07:59:59; 08:00:00-11:59:59; 12:00:00-15:59:59; 16:00:00-19:59:59; 20:00:00-23:59:59). The average is taken over the days in July. You need to report **SIX** numbers, one for each of these four-hour slot.

B. Visualise the results in A above as a figure.

C. Find out the top 20 most requested **“.html”** files (i.e. rows containing **“xxx.html”**, where **xxx** is the filename, **.html** is the file extension). Report the file name and number of requests for each of these 20 files (pages).

D. Visualise the results in C above as a figure.

# Movie Recommendation
**Data**:
the *[MovieLens 25M Dataset](https://grouplens.org/datasets/movielens/25m/)*. 
Please read the *[dataset description](http://files.grouplens.org/datasets/movielens/ml-25m-README.html)* to understand the data and complete the following four tasks.

A. Perform a **three-fold cross validation** of ALS-based recommendation on the rating data **ratings.csv**. Study **three** versions of ALS: one with the ALS setting used in Lab 3 notebook, and another **two different settings decided by you**. For each split, compute the Root Mean Square Error (RMSE) and Mean Absolute Error (MAE) for the three ALSs. Then compute the mean and standard deviation (std) of RMSE and MAE over the three splits. Put these RMSE and MAE results for each of the three splits as well as the mean & the std in one Table for the three ALSs in the report (2 x 5 x 3 = 30 numbers in total). Visualise the mean and std of RMSE and MAE for each of the three versions of ALS in one single figure. 

B. After ALS, each movie is modelled with some factors. Use *k-means* with **k=25** to cluster the movie factors (**hint**: see **itemFactors** in ALS API, id=movieid in this problem). For each of the three split, use **genome-scores.csv** to find the top three tags for each of the **top three** largest clusters (i.e., 9 tags in total for each split), find out the names of these top tags using **genome-tags.csv**, and count the number of movies having each of these three tags in each cluster (one number per tag per cluster). For each cluster and each split, report the top three tags and the respective number of movies having that tag in one table. **Hint**: For each cluster, sum up tag scores for all movies in it; find the largest three scores and their indexes; go to genome-tags to find their names.


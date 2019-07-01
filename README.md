# DATA_SCIENTIST_Movie_recommendations
This project is part of the Openclassrooms DataScientist Curriculum together with CentraleSupélec

### by Jérôme d'Harveng


## Dataset

> For this project, we could use an IMDB movie database with different features of over 5000 movies (such as cost, earnings, rating,…). The **goal** was here given the title of a movie to recommend 5 other movies interesting for the user.

## Feature Engineering:
> _Feature engineering_ was needed for example for the **content_rating** to join all the redundant ratings together.
We added also the **revenue**, being the _difference between gross and budget_ as new feature, aswell as **success** being the _ratio between revenue and budget_.

## Data exploration:
> After having cleaned the data, and before moving to the recommendation system itself, we first did some exploration to get a better understanding of our data.

> _Some interesting insights were:_
> - Even if movies in this DB are from 1927 till 2016, 75% of them were produced after 1999.
> - Logically 96% of the movies are in color and almost 80% of them were produced in the US, with as consequence that more than 95% of the movies are in English.
> - The longest movie of the DB is « _Blood in, Blood Out_ » lasting over 5h30min.
> - The movie having the biggest gross is "_Avatar_" with 760M$
> - The average _IMDB_score_ is round 6.5 and the movie with the best score (of 9.3) is « _The ShawShank Redemption_ »
> - The 2 movies with the biggest _success ratio_ (revenue/budget) are « _Paranormal Activity_ » and « _the Blair With Project_ »

## Recommendation system:
> - We tried several **dimensional reduction technics** on the cleaned data, in order to allow _proper visualisation_ and to improve the performances of the algorithms. The **PCA** technic didn’t seem well suited in our case so we used **t-SNE**.
> - From the reduced data, we applied a _clustering algorithm_.
Here we used _K-means++_ and used the « _silhouette coefficient_ » to find the proper amount of clusters.
> - Within the cluster corresponding to the movie we are searching recommendations for, we searched _similarities intracluster_. Here we used « _cosine similarity_ » as measure.


> So our recommendation system works finally as followed:
1. Find the cluster label related to the movie we are searching for
2. Take the complete cluster corresponding to this label
3. Within this cluster, compute the cosine similarity
4. Take the 5 movies with the highest similarity scores.

Here we did what’s called **« Content Filtering »**, everyone is getting the same recommendations. This is opposed to _« collaborative Filtering »_, where we need also information about the users.

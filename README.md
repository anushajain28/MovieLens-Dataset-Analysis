# MOVIELENS Data Analysis

## Introduction

MovieLens is a research site run by GroupLens Research at the University of Minnesota.It contains 20000263 ratings and 465564 tag applications across 27278 movies. These data were created by 138493 users between January 09, 1995 and March 31, 2015. This dataset was generated on October 17, 2016.

The data contains Tag Genome Data.The tag genome encodes how strongly movies exhibit particular properties represented by tags (atmospheric, thought-provoking, realistic, etc.). The tag genome was computed using a machine learning algorithm on user-contributed content including tags, ratings, and textual reviews.

## Data Source 
[MovieLens Data](https://grouplens.org/datasets/movielens/ "MovieLens Data Link")
[MovieLens + Rotten Tomatoes](https://grouplens.org/datasets/hetrec-2011/ "MovieLens+Rotten Tomatoes Link")

## Data Processing and Cleaning
- Some of the files downloaded were in .dat format.
- Run a python code to convert the .dat files to .csv files
- After converting the files, give proper column names to columns based on the structure
of data in .dat file.
###Data linkage
- The data in the various files are linked through movieID, userID, TagID.

## Analysis 
When analyzing movies the first things that comes to mind about movies is the "Rating" of a movie.Atleast once before going for a movie, a viewer checks it rating. One is keen to know how the viewers have rated the movie and how is the movie rated by the critics.
Analyzing the ratings by viewers and critics gives us an idea about how the movie might be.

## Analysis 1 : 
-Identifying the variation in ratings of users/viewers and critics. 
-Based on the analysis find the top 5 movies which maintained a balance between users and critics. And the top 5 movies which were highly divisive.

### Steps followed: 
    
- read the files movies.csv, rating.csv which has user ratings and movies_1.csv which has critics ratings in different dataframes.
- cleaning the data of input file. Removing all records having '\\N' as values. 
- converting ratings and number of critics to float so that can be used comparison
- for the analysis I have taken into consideration only those movies which were rated by atleast 30 CRITICS. And the movie which were rated by atleast 500 users. 
- the critics rating are converted to equvalent of 5 so it can be compared to ratings by users. 
-calculate the weighted mean rating of users by using the following formula
	- weighted rating = (v/(v+m))R+(m/(v+m))C
	- where:
	- R = average for the movie (mean) = (Rating)
	- v = number of votes for the movie = (votes)
	- m = minimum votes required to be listed in the Top 50 (currently 500)
	- C = the mean vote across the whole report
-combing the dataframes of users and critics rating we get the following dataframes
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_1/rating_df.JPG)
    
### Results:
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_1/ratings_variation.jpeg)

From the plot we see that over the period of years, the ratings from users have fluctuated in a limited range of 2.5-4.2 where as for the same movies the critics have rated as low as 1.0 and and as high as 4.7 . The users rate the movie mostly on the basis of story content where critics rate the movie based on every aspect and hence this variation in ratings. 

##### Highly divisive movies
- movies that have been made only either for masses with spice in stories or the movies that have been made from the perspective of critics and judges. 
- such movies have high variation in user and critics ratings
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_1/divisive_movies.jpeg)

##### Balanced Movied
- movies that have been made keeping in mind to maintain balance between users, critics and judges. 
- such movies have very low variation in user and critics ratings
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_1/balanced_movies.JPG)

### Conclusion
From the plot we see that over the period of years, the ratings from users have fluctuated in a limited range of 2.5-4.2 where as for the same movies the critics have rated as low as 1.0 and and as high as 4.7 . The users rate the movie mostly on the basis of story content where critics rate the movie based on every aspect and hence this variation in ratings. 

====== 

## Analysis 2
- User write tags for the movies. using that tags we can determine how strongly movies exhibit particular properties represented by tags (atmospheric, thought-provoking, realistic, comdecy,etc.)
- According to the tags associated with movies we can recommend similar movies to a user based on his search for a particular movie. 

    
### Steps followed: 
    
- read the following file : movies, tags, ratings, genome-tags, genome-scores and join them to form a single dataframe
- for a movie, take tags whose tag relevance score is greater that 0.5 for that movie
- for each movie create a list of its associated tag and store in dictionary.
- when the user inputs a movieID, if the movieID is present in dataset, then movies related to the input movie,based on the tags assocciated with each movie, is recommened
to user.
    
    
### Results:

#### Input 1: Movie ID : 19
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_2/user_input_1.JPG)
#### Related Movies
![alt tag](
https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_2/related_movies_df_1.JPG)

![alt tag](
https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_2/related_movies.jpeg)

##### Input 2: Movie ID : 628
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_2/user_input_2.JPG)

##### Related Movies
![alt tag](
https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_2/related_movies_df_2.JPG)

![alt tag](
https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_2/related_movies_2.jpeg)

======

## Analysis 3
For each movie, there are n number of users who have rated the movie.
- Determining the most favourite genre for an age-group.
- For each genre, how the males and females have rated the genre.  
    
### Steps followed: 
    
- read the files: ratings, users, movie_genres.
- from the users file bin the users into age-groups '0-9','10-19', .... '70-79'.
- Group the dataframe by age-group and find the most favourite genre for each group. 
- Group the dataframe by genre, and find out the mean rating by each gender for each genre.
        
### Results:

##### Most Popular Genre for each Age-Group
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_3/age_group_genre.jpeg)

##### Mean Rating for each Genre by each gender
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_3/gender_rating_genre.jpeg)

### Conclusion
From the above plot we can conclude that majority of users rating the movies belong to age-group: 20-60 and majority of users are fond of DRAMA movies. 

======

## Analysis 4
Based on the choice of movies by users, there has been a considerable amount of change in the number of movies produced for each genre every year. 
- Analyzing the trend of movies produced every year.  
    
### Steps followed: 
    
- read the file movies.csv
- split the genres for each movie and create a column for genre.
- calculate the sum of movies produced for each year in each genre.
        
### Results:

##### Movies produced each year for each genre
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_4/movies_every_year.jpeg)

##### Trend of movies produced in various genres over the period of years
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_4/movies_trend.jpeg)

### Conclusion
From the graph , it is evident that the genres for which procduction has changed significantly over the period of years are **DRAMA** , **COMEDY** , **Action**. Also from the previous analysis it was interpreted that the most favourite genres for different age groups are same : Drama, Comedy and Action. And hence there is an increase in procduction

======

## Analysis 5
- Based on movie ratings, identifying the top 10 directors. 
- For the top 10 directors, identify the favourite shooting location.  
    
### Steps followed: 
    
- read the files: movie ratings, movie directors and movie locations 
- find the average rating for each movie
- for each movie there is a director and the rating applies to director as well.
- group by director and find the mean of ratings for each director. 
- sort by ratings is descending order and the top 10 records give the top 10 directors.

- For those top 10 directors, find the shooting locations
- Find the number of movies shot at each location.
- The location with the max number of movies is most favorite loaction for the director.
        
### Results:

##### Top 10 directors and their ratings
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_5/top10directors.jpeg)

##### Favorite shooting locations of top 10 directors
![alt tag](https://github.com/anushajain28/Final_Exam_2017/blob/master/Analysis/Analysis_5/favourite_location.jpeg)

### Conclusion
Analysing the movieLens dataset gave many interesting insights into the movie business. Although it is mainly used for recommendation systems we were still able to extract some trends in the data.

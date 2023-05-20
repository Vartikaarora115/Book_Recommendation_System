# Book_Recommendation_System
# <h3>Problem Statement</h3>
During the last few decades, with the rise of Youtube, Amazon, Netflix, and many other such web services, recommender systems have taken more and more place in our lives. From e-commerce (suggest to buyers articles that could interest them) to online advertisement (suggest to users the right contents, matching their preferences), recommender systems are today unavoidable in our daily online journeys.


In a very general way, recommender systems are algorithms aimed at suggesting relevant items to users (items being movies to watch, text to read, products to buy, or anything else depending on industries).


Recommender systems are really critical in some industries as they can generate a huge amount of income when they are efficient or also be a way to stand out significantly from competitors.

The main objective is to create a book recommendation system for users.

<h3>Project Summary</h3>
A Book Recommendation System which recommends the users a selection of books based on their interests.

<h4>1. Data loading, Cleaning and Pre-Processing:</h4>
The dataset consists of three dataframes; Books, Users, and Ratings. Data from all three tables are cleaned and preprocessed separately as defined below briefly:

<h4>For Users Table:</h4>

Checked for null values in the table. The Age column has more than 1 lakh null values. Check for unique values present in the Age column. There are many invalid ages present like 0 or 244. By keeping the valid age range of readers as 10 to 80 replace null values and invalid ages in the Age column with the mean of valid ages. The location column has 3 values city, state, and country. This column has been treated and only country information is kept for further analysis. There were some absurd values and misspelled country names in country column which were treated. Duplicate entries were dropped from the table



<h4>For Books Table:</h4>

Droped all three Image URL features.

Checked for the unique years of publications. Two values in the year column are publishers. Also, for three tuples name of the author of the book was merged with the title of the book. Manually set the values for these three above obtained tuples for each of their features using the ISBN of the book. Convert the type of the years of publications feature to the integer.

By keeping the range of valid years as less than 2004 and not 0, replace all invalid years with the median of the publication year.



<h4>For Ratings Table:</h4>

Checked for null values in the table. Check for Rating column and User-ID column to be an integer. Removal of punctuation from ISBN column values and if that resulting ISBN is available in the book dataset only then considering else drop that entity.

Divided the data in two dataframe having explicit(non zero ratings)and implicit ratings.

Checked for missing values ,there were none. Added a column of average rating of the book to the dataframe.


  <h3>2. Algorithms Implemented:</h3>
  <h5>2.1 Popularity Based Recommendation :</h5>

Recommendation using Average Weighted Rating We have calculated the weighted score using the below formula for all the books and recommended the books with the highest score.

score= t/(t+m)∗a + m/(m+t)∗c

where, t represents the total number of ratings received by the book m represents the minimum number of total ratings considered to be included a represents the average rating of the book and, c represents the mean rating of all the books.

2.3 User-Item Collaborative Filtering Recommendation Collaborative Filtering Recommendation System works by considering user ratings and finds cosine similarities in ratings by several users to recommend books. To implement this, we took only those books' data that have at least 50 ratings in all.

<h5>2.2 Nearest Neighbour Based Recommendation:</h5>

To train the Nearest Neighbours model, we have created a compressed sparse row matrix taking ratings of each Book by each User individually. This matrix is used to train the Nearest Neighbours model and then to find n nearest neighbors using the cosine similarity metric.

<h5>2.3 Correlation Based Recommendation:</h5>

For this model, we have created the correlation matrix considering only those books which have total ratings of more than 100 and users who have rated more than 5 books. Then a user-book rating matrix is created. For the input book using the correlation matrix, top books are recommended.

<h5>2.4 Singular value decomposition collaborative filtering( User-Item):</h5>

SVD which is a Latent factor model is used which compresses user-item matrix into a low-dimensional representation in terms of latent factors and can handle the sparsity of the original matrix. Recommendations are made on basis of users prior preference with respect to a book item.

<h5>2.5 Content Based Recommendation:</h5>

In this again a dataset is used in which books having total ratings of more than 100 and users who have rated more than 5 books is used. Book title text is converted into a vector structure, and recommendations are made on basis of which book title seems more related with the selected book.

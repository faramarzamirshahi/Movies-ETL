# Movies-ETL
UofT Data Analytics

# Overview
The project gathers data from both Wikipedia and Kaggle, combines them, and saves them into a SQL database so that it's available as a clean dataset for the end user.
MovieLens is a website run by the GroupLens research group at the University of Minnesota. The Kaggle dataset pulls from the MovieLens dataset of over 20 million reviews and contains a metadata file with details about the movies.

# Details
The process Extracts, transforms and loads (ETL) the three files below.

* **movies_metadata.csv**
MovieLens is a website run by the GroupLens research group at the University of Minnesota. 
The [Kaggle dataset](https://www.kaggle.com/rounakbanik/the-movies-dataset/download) 	pulls from the MovieLens dataset of over 20 million reviews and contains a metadata file with details about the movies from The [Movie Database (TMDb)](https://www.themoviedb.org/)
* **ratings.csv**
ratings data from MovieLens on Kaggle
* **wikipedia-movies.json**
Wikipedia has a ton of information about movies, including budgets and box office returns, cast and crew, production and distribution, and so much more.
[wikipedia-movies.json](https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-online/module_8/wikipedia-movies.json) is a compilation of records pulled from wikipedia and formatted in json.

[ETL_create_database.ipynb](https://github.com/faramarzamirshahi/Movies-ETL/blob/main/ETL_create_database.ipynb) steps:<br>

1- Select only the records from wikipedia-movies.json that have 'imdb_link' and ('Director' or 'Directed by') keys and 	not 'No. of episodes'<br>
2- Combine titles in various languages into one single field<br>
3- Derive the 'imdb_id' from 'imdb_link' and use this as the primary key to de-duplicate records<br>
4- Drop fields that are 90% empty<br>
5- Convert the fields into appropriate data types using regular expressions<br>
6- Remove the 'adults' films from the kaggle data and convert fields into appropriate data types<br>
7- Merge the wikipedia dataset with kaggle data, select/update/drop fields that exist in both sets<br>
8- Get the count on the ratings data by movieId and rating. Then pivot the group using movieId as Index, rating as column and the count as value<br>
9- Merge dataset in step #7 with the one on step #8<br>
10- Load dataset in step#7 into the SQL database<br>
11- Load ratings dataset into SQL database


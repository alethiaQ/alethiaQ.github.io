---
layout: post
title:      "Flicks- Rails Project and AR Association setup"
date:       2019-10-18 20:14:03 +0000
permalink:  flicks-_rails_project_and_ar_association_setup
---


For our third project, we were tasked with creating any management rails application. I chose to make a simple in concept, but complicated in procedure **Movie management app**. **Flicks** is designed for users who enjoy films and have a large collection of them. Users of Flicks are able to either search for an existing movie or log one manually and add it to their **collection**, allowing users to keep track of the movies they own and their forgetful details such as actors, director, description, release date and genre. Flicks also **recommends upcoming movies**, along with their trailers and details, to Users based on their favorite genres. 

For me, the hardest and more confusing aspect of creating an application is relating objects and their data. Although, it can be a difficult task, ActiveRecord associations are one of the most important pieces of a fluid app. So, it is cruicial that relationships are set up correctly, preventing data from being misplaced or invalid. 

Flicks is a movie based app based on User interaction so the most basic models needed are- 
* User 
* Movie 
* Genre (to categorize movies) 

**Basic Relatioships**- 
* User has many movies 
* Movie has many genres 
* Genre has many movies 

As you can see, currently the basic models all have many to many relationships so.... 
**JOIN TABLES**- 
* UserMovies - belongs to user and movie
* MovieGenres - belongs to movie and genres 
* UserGenres- belongs to user and Genres (for recommended movies to user by genres) 

After relating our basic models through joins tables, our final scheme is- 
* User- *has many movies through user movies, has many genres through user genres*
* Movie- *has many genres through movie genres, has many users through user movies*
* Genre- *has many movies through movie genres, has many users through user genres*
* UserMovie- *belongs to user, belongs to movie*
* UserGenre- *belongs to genre, belongs to user*
* MovieGenre- *belongs to movie, belongs to genre*

Once relationships are set up accordingly,
* Users are able to access their collection of movies by ***username.movies => []***, and 
* movies are recommended to users through ***username.genres.each do |genre|               genre.movies => [Returns a collection of all movies within that genre]*** and
*  Movies can have multiple genres ***movie.genres => ["Romance", "Comedy"]*** 




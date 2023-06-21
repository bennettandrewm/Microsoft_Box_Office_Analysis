# BREAKING DOWN THE BLOCK BUSTERS
## Analysis of Top Grossing Movies in Theaters of Last 20 years
### Author: Andrew Bennett

## Project Overview
To aid Microsoft in its voyage into movie making, this repository contains all the files related to an analysis of approximately 2,000 movies of the last 20 years, including all databases, csv files, and other supporting documents. The purpose was to provide concrete recommendations that could be used to launch a movie studio. Based on the analysis of reliable industry databases (IMDB and *The Numbers*), the analysis recommends focusing on movies with a production budget of $30-45M, hiring directors with a track record of profitable films in this range (our ranking is included below), and to be genre agnostic, meaning make a broad swath of movies.

![Movie_Image.jpg](attachment:Movie_Image.jpg)

*"The business of film is to make dreams into reality so audiences can escape for a few hours."* 

### Business Problem

Microsoft sees all the big companies creating original video content and decided to create a new movie studio. The problem? They've never done this before, and don't know the first thing. But that's never stopped anyone before. 

So how do we learn what movies to make now that will perform in the future? Let's study the past. Specifically, the box office success of all the movies of the last 20 years. If we can glean insight into what goes into making successful movies, we can reproduce the blockbusters that come out.

So, we're going to access some publically available datasets and focus our analysis on three major variables in moving making.

* genre
* budget
* directors

These factors represent some of the simplest, most foundational decisions. Genre determines which scripts and creative teams you'll need. The budget is the money you'll need upfront to greenlight a project. And the director is the creative lead who will shepard the day-to-day movie-making and ultimately deliver the project to you and your audience.

Lucky for us, the information is readily available. But what specifically are we going to measure? To gauge financial success, we're going to examine both Return on Investment (ROI) and the profit margin on the Worldwide Gross Revenue, which we'll call Gross_Margin. ROI is just the multiplier from the Worldwide Gross Revenue divided by the production budget. So, an ROI > 1 means a movie made a profit. ROI < 1 and the movie lost money. Gross_Margin is Worldwide Gross Revenue minus production budget. This majors how much profit, in dollars, was made compared to the movies cost to produce.

These will be the two financial performance metrics we'll use to compare against the genre, budget, and directors. We should take a second to note that we have not factored in marketing or distribution costs into either ROI or Gross Margin. This data is not as readily accessible on this scale. These costs are also not known BEFORE a movie is greenlit, so it's hard to consider these costs as inputs, however they do affect the REAL profits of a movie studio when they're all accounted for.

So let's begin...

## Data Understanding and Analysis
### The Data Source

To solve this problem we used well-known industry resources where are included in this repository in the folder `zippedData`. These files contain movie datasets from the following publicly available websites:

* [Box Office Mojo](https://www.boxofficemojo.com/)
* [IMDB](https://www.imdb.com/)
* [Rotten Tomatoes](https://www.rottentomatoes.com/)
* [TheMovieDB](https://www.themoviedb.org/)
* [The Numbers](https://www.the-numbers.com/)

As we dug into the files, we eventually use two sources to perform our analysis. 

* `im.db.zip`
  * Zipped SQLite database (this was unzipped in the BASH window using the unzip command)
* `zippedData/tn.movie_budgets.csv.gz`
  * Compressed CSV file (opened using `pd.read_csv` in the Jupyter Notebook)

The IMDB movie database (https://www.imdb.com/) is one of the most complete, publically box office available databases. It's a well known industry staple and incredibly robust. However, We also need budget information, and that's what we'll get from The Numbers (https://www.the-numbers.com/) which reports daily and weekly box office sales for movies currently in release. From there, we examine the movie titles, genres, production budgets, directors and their respective gross box office receipts.

The following diagram was useful for the analysis with the IMDB database. It shows the heirarchy of the database we used.

![movie data erd](https://raw.githubusercontent.com/learn-co-curriculum/dsc-phase-1-project-v2-4/master/movie_data_erd.jpeg)

### RESULTS

#### GENRE
To examine genre, the goal was to find a correlation between the roughly 20 or so categories and the financial metrics, ROI in particular. When we correlated, what we find is... no correlation.

![Genre.jpg](attachment:Genre.jpg)

####  - GRAPH 1 - Correlation Factors of Genre on ROI.
Generally, a correlation factor between 0.25-0.50 is considered weak. So, what about correlation factors below that? I wouldn't make any big bets based on that. It's clear that there is a minor correlation with Mystery and Horror between ROI, but not enough to launch a horror stuido. If there is any take away, is that there's a slightly negative correlation with Drama. Because we're considering Worldwide Gross, perhaps Dramas don't translate overseas the way other more thrilling, scary, or upbeat movies might.

#### BUDGET
To examine budget, we wanted to see if there was any range of budget that seemed to perform better than any other. To do this, we created budget categories and measured the distribution of these categories against the ROIs.

Is it the microbudget suprise hit? The big budget blockbuster? Actually... it's the midbudget monster!

![Budget.jpg](attachment:Budget.jpg)

### Graph 2 - Distribution of Movies by budget with ROI greater than 1

There are many more budgets in the $30-45M range that have an ROI greater than 1 than any other budget range. Why? It's difficult to say now, and we really don't know. One thought is that this is the lowest budget range that allows for top-level talent to be hired. So, speaking of talent, who's going to lead this thing. 

#### Directors
To determine who are the best directors, we wanted to see who had the best track record in the budget range. We found all of the directors who made AT LEAST 2 movies in this range, and looked at their average profit. In other words, we ranked these directors in descending order based on mean Gross Margin. Voila!

![Directors.jpg](attachment:Directors.jpg)

### Graph 3 - Directors with Best Average Margins in the $30-45M range

The top performing directors are Paul Feig, Olivier Megaton, Jon M.Chu, Seth Gordon, and Ben Affleck. Paul Feig makes hysterical comedies, Olivier Megaton makes high octane action movies (Transporter series), Jon M.Chu makes beautiful glossy romance and musicals. Seth Gordon ... also hysterical comedies. Ben Affleck is, well, Ben Affleck. Ben is Ben. Or... he's one half of Bennifer... depending on the decade.

The point stands that, the successes here are definitive with the top 5 directors averaging a Gross Margin of over $150M on a midbudget movie. The genre is varied.



  

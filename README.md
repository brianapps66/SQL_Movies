# SQL_Movies

Creates an SQL database from data supplied by the MovieLens website (http://movielens.org).

MovieLens is a movie recommendation website that uses collaborative filtering to choose the movies that a user is most likely to enjoy.

The data is available from the GroupLens Research website here: http://grouplens.org/datasets/movielens. I am working with the "u.item" file, which contains the details of each movie, such as the year of release and what genre it is in.

The dates in the data are not in a date-readable format for SQL, so first the data is run through the movielens_dates.py Python program. This creates a new file with the dates rewritten in a suitable format.

The SQL table is created using the following commands:

    CREATE TABLE movies(
		movie_id INT PRIMARY KEY,
		movie_title TEXT NOT NULL,
		release_date DATE,
		video_release_date DATE,
		imdb_url TEXT,
		unknown BOOLEAN NOT NULL,
		action BOOLEAN NOT NULL,
		adventure BOOLEAN NOT NULL,
		animation BOOLEAN NOT NULL,
		childrens BOOLEAN NOT NULL,
		comedy BOOLEAN NOT NULL,
		crime BOOLEAN NOT NULL,
		documentary BOOLEAN NOT NULL,
		drama BOOLEAN NOT NULL,
		fantasy BOOLEAN NOT NULL,
		film_noir BOOLEAN NOT NULL,
		horror BOOLEAN NOT NULL,
		musical BOOLEAN NOT NULL,
		mystery BOOLEAN NOT NULL,
		romance BOOLEAN NOT NULL,
		sci_fi BOOLEAN NOT NULL,
		thriller BOOLEAN NOT NULL,
		war BOOLEAN NOT NULL,
		western BOOLEAN NOT NULL
    );

`.separator "|"`

`.import u_date_adjusted.item movies`


Some sample queries that can be run on the table:

-To find the movies that were released in 1994:

`SELECT movie_title FROM movies WHERE release_date BETWEEN date('1994-01-01') AND date('1994-12-31');`

-To find all movies that are in both the sci-fi and comedy genres:

`SELECT movie_title FROM movies WHERE sci_fi and comedy;`

-To find all the titles and IMDB URLs for movies that contain the word "Day" in the title:

`SELECT movie_title, imdb_url FROM movies WHERE movie_title LIKE "%day%";`

-To find the number of horror films:

`SELECT COUNT(*) FROM movies WHERE horror;`




This project will be updated to include the user data in the table.

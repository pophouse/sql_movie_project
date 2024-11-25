# SQL Exam Using TMDB Movie Database
### overview
This project is a simple implementation of a movie database engine using Structured Query Language (SQL). The main objective of the project is to demonstrate how to create and connect a database engine, interact with the database, and execute SQL commands to retrieve and display data.

The project uses SQL to manage a movie database, which stores information such as movie titles, directors, actors, genres, and release dates. The engine connects to a database and executes SQL queries to print out the tables and display information.

### Database Structure
The TMDB movie database includes several tables related to movies, actors, directors, genres, awards, and more. Some key tables you will be interacting with include:

1. movies: Contains information about movies, including movie ID, title, release year, and genre.
2. actors: Contains data about actors, including their ID, name, and bio.
3. directors: Contains information about directors.
4. genres: Contains genre details.
5. awards: Includes awards and nominations related to movies and actors.
For this exam, you will need to write SQL queries using the provided database schema to answer the questions.
### features Demonstrated
##### Querying and Filtering
- SELECT: Retrieve specific columns of interest from the database.
- WHERE: Filter data based on conditions (e.g., movies released after 2000).
- LIKE: Search for patterns (e.g., movies starting with "The").
- BETWEEN: Filter numeric or date ranges (e.g., movies rated between 7 and 9).
#### Sorting and Limiting
- ORDER BY: Sort results by columns (e.g., highest-rated movies first).
- LIMIT: Restrict the number of rows returned by a query (e.g., top 5 movies).
- Aggregation and Grouping
- COUNT: Count rows or specific entries in a dataset (e.g., total movies).
- COUNT(DISTINCT): Count unique values (e.g., distinct genres in the dataset).
- GROUP BY: Group data to apply aggregate functions (e.g., average rating per movie).
##### Joining Tables
- INNER JOIN: Fetch related records from multiple tables (e.g., movies and their directors).
- LEFT JOIN: Include all records from the left table, even if there's no match in the right table (e.g., movies with or without ratings).
##### Data Manipulation
- UPDATE and SET: Modify existing records (e.g., updating a movie’s average rating).
- CREATE VIEW: Simplify complex queries by creating reusable views (e.g., a view for top-rated movies with director names).

### Requirements
To run this project, you will need the following:

Python 

SQLite (or any relational database system of your choice)

Basic understanding of SQL

### Installation
1. Clone the Repository
```bash

git clone <https://github.com/pophouse/sql_movie_project.git>
cd sql_movie_project
```
2. Set Up the Environment
We recommend using a virtual environment for better dependency management:

```bash

python3 -m venv venv
source venv/bin/activate  # On Windows, use venv\Scripts\activate
```
3. Install Dependencies
For this project, SQLite is used, and no external Python packages are required. If you want to connect to other databases like PostgreSQL or MySQL, install the appropriate libraries (e.g., psycopg2 for PostgreSQL).

```bash

pip install sqlite3  # SQLite is built-in, so this step is optional
```
### Sample Queries
###### Retrieve top 10 highest-rated movies:
```bash

SELECT title, AVG(rating) AS average_rating
FROM movies
JOIN ratings ON movies.id = ratings.movie_id
GROUP BY title
ORDER BY average_rating DESC
LIMIT 10;
```
Find movies released between 2000 and 2010:
```bash

SELECT title, release_date
FROM movies
WHERE release_date BETWEEN '2000-01-01' AND '2010-12-31'
ORDER BY release_date;
```
###### List all movies with a title containing "Love":
```bash

SELECT title, release_date
FROM movies
WHERE title LIKE '%Love%'
ORDER BY release_date DESC;
```
###### Count the number of unique users who rated movies:
```bash

SELECT COUNT(DISTINCT user_id) AS unique_users
FROM ratings;
```
###### Create a view for top-rated movies with director details:
```bash

CREATE VIEW top_rated_movies AS
SELECT movies.title, AVG(ratings.rating) AS average_rating, directors.name AS director
FROM movies
INNER JOIN ratings ON movies.id = ratings.movie_id
INNER JOIN directors ON movies.director_id = directors.id
GROUP BY movies.title, directors.name
ORDER BY average_rating DESC;
```
###### Retrieve data from the view:
```bash

SELECT * FROM top_rated_movies LIMIT 5;
```
### Author
Email: <preciousjames468@gmail.com>
Username: Pophouse

### Contributing
Feel free to fork the repository, submit issues, and make pull requests. Contributions are welcome!

### Conclusion
By completing the SQL queries, you will demonstrate your ability to interact with a relational database and apply SQL concepts like JOIN, WHERE, COUNT, and DISTINCT to analyze and retrieve information from the TMDB movie database.
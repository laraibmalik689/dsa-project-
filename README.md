CREATE TABLE User(
user_id INT PRIMARY KEY AUTO_INCREMENT ,
name VARCHAR(100) NOT NULL,
email VARCHAR(100) UNIQUE NOT NULL,
age INT,
Gender VARCHAR(100);
CREATE TABLE Movie(
movie_id INT PRIMARY KEY AUTO_INCREMENT, 
title VARCHAR(255) NOT NULL,
release_year YEAR,
description TEXT,
duration INT);
CREATE TABLE Genre
(genre_id INT PRIMARY KEY AUTO_INCREMENT, genre_name 
VARCHAR(100) NOT NULL);
CREATE TABLE Movie_Genre 
(movie_id INT,
genre_id INT,
PRIMARY KEY(movie_id,genre_id),
FOREIGN KEY(movie_id) REFERENCES Movie(movie_id), FOREIGN 
KEY(genre_id) REFERENCES Genre(genre_id));
CREATE TABLE Rating( 
rating_id INT PRIMARY KEY AUTO_INCREMENT,
user_id INT,
movie_id INT,
rating INT,
rating_date DATE,
FOREIGN KEY(user_id) REFERENCES User(user_id), FOREIGN 
KEY(movie_id) REFERENCES Movie(movie_id));
INSERT INTO User(name,email,age,gender) 
VALUES 
('Alice','alice@example.com',25,'female'), ('Bob','bob@example.com',30,'male');
INSERT INTO Movie(title,release_year,description,duration) VALUES 
('Inception',2010,'A mind-bending thriller',148),
('The Matrix',1999,'Neo discovers the truth',136);
INSERT INTO Genre(genre_name) 
VALUES 
('Sci-Fi'),
('Action');
INSERT INTO Movie_Genre(movie_id,genre_id)
VALUES 
(1,1),
(1,2),
(2,1); 
INSERT INTO Rating(user_id,movie_id,rating,rating_date) VALUES 
(1,1,5,'2025-06-01'),
(2,1,4,'2025-06-02'), 
(1,2,5,'2025-06-03');
ALTER TABLE Movie ADD COLUMN language VARCHAR(50);
ALTER TABLE User MODIFY COLUMN name VARCHAR(150);
ALTER TABLE Genre DROP COLUMN genre_name; ALTER TABLE Rating 
ADD COLUMN review TEXT;
INSERT INTO User(name,email,age,gender) 
VALUES ('Charlie','charlie@example.com',28,'other'); UPDATE Movie SET 
duration=150 WHERE title='Inception'; DELETE FROM Rating WHERE 
rating<3;
SELECT * FROM User;
SELECT name, title, rating
FROM User, Movie, Rating
WHERE User.user_id = Rating.user_id AND Movie.movie_id = Rating.movie_id;
SELECT title, release_year
FROM Movie
WHERE release_year > 2005;
SELECT title
FROM Movie, Rating, User
WHERE Movie.movie_id = Rating.m

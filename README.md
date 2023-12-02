# Mid-Term-MogoDB

========================================================================================================================================
========================================================================================================================================
****************************************************************************************************************************************
****************************************************************************************************************************************
========================================================================================================================================
========================================================================================================================================

## 1. Fetch all the document from movie collection.
 db.movie.find().pretty();
## 2. Fetch all the document with director firstname “Richard”.
 db.movie.find({"director.first_name":"Clint","director.last_name":"Eastwood"}).pretty();
do the same thing for all questions
========================================================================================================================================
========================================================================================================================================
****************************************************************************************************************************************
****************************************************************************************************************************************
========================================================================================================================================
========================================================================================================================================
========================================================================================================================================
Create an Assignment database.
Copy all the script from movie_Script.txt file and execute on the Mongo DB server under Assignment database.
A. Write the following script to fetch the document on movie collection.
 
### 1. Fetch all the document from movie collection.
 db.movie.find()
### 2. Fetch all the document with director firstname “Richard”.
 db.movie.find({ "director.first_name": "Richard" })
### 3. Fetch all the document with director “Eastwood Clint”.
 db.movie.find({“director.first_name )
### 4. Fetch all the document with actor “Bruce Willis”.
 db.movie.find({“actors.first_name”: “Bruce”, “actors.last_name”: “Willis”})
### 5. Fetch all the document with director birthdate is older than 1900.
 db.movie.find({year: {$gte: 1990, $lte: 1999}})
### 6. Fetch all the document with movies released in the 90s.
 db.movie.find({ year : {$gte: 1990. $lt: 2000})
### 7. Fetch all the document with movies released before the year 2000 or after 2010.
 db.movie.find($or: [{date: {$lt: 2000)}, {date: {$gte: 2011}}]})
### 8. Fetch all the movie distinct title.
 db.movie.distinct("title") 
### 9. Count the number of movies released in USA.
 db.movie.find({country: “USA”}) 
### 10. Count the movie released between year 1990 to 1995.
 db.movie.find({year: { $gte: 1990, $lte: 1995 } })
### 11. Fetch all the country where movies released.
 db.movie.distinct(“country”)
### 12. Fetch all the document with movies titled as “Gladiator”.
 db.movie.find({ title: "Gladiator" }) 
### 13. Fetch distinct genre values of movies.
 db.movie.distinct(“genre”) 
### 14. Fetch all the document with movie “crime" or "drama" genre.
 db.movies.find({ genre: { $in: ["crime", "drama"] } })
### 15. Fetch all the movies directed by "Hitchcock", display only title and year and sort them by year.
 db.movies.find( { "director.last_name": "Hitchcock" },{ _id: 0, title: 1, year: 1 }).sort({ year: 1 })
### 16. Fetch the list of movies where "Cotillard" played. 
 db.movie.find({“actors.last_name”: “Cotillard”}, {“title”: 1, “_id”: 0})
### 17. Fetch the list of movies released between 1967 and 1995.
 db.movie.find({year : { $gte: 1967, $lte: 1995} })
### 18. Fetch the list of movies released between 1967 and 1995, by displaying only title, year, director’s last name sorted by year.
 db.movie.find( { year: { $gte: 1967, $lte: 1995 } }, { _id: 0, title: 1, year: 1, "director.last_name": 1 }).sort({ year: 1 })
### 19. Fetch the number of movies by country.
 db.movie.aggregate([{ $group: { _id: "$country", count: { $sum: 1 } } },{ $sort: { count: -1 } }])
### 20. Fetch the number of movies by country and actor.
 db.movie.aggregate([{ $group: { _id: { country: "$country", actor: "$actors.last_name" }, count: {$sum: 1 } } },{ $sort: { "_id.
country": 1, count: -1 } }])
========================================================================================================================================
## B. Write the script to update document on movie collection.
1. Update the movie with title “The Titanic” from “Titanic” where _id is "movie:3".
 db.movie.updateOne({_id: “movie:3” , title: “Titanic”}, {$set: {title: “The Titanic”}})
2. Update the movie with genre “The Comedy” from "Comédie" where _id is “movie:7”.
 db.movie.updateOne({_id: “movie:7”, genre: “Comédie”} {$set:{genre: “The comedy}}) 
3. Update the movie with year 1990 from 1999 where _id is "movie:6".
 db.movie.updateOne({_id: “movie:6” , year: 1999} {$set:{year: 1990}}) 
4. Update the movie with country “FR” from "USA" where _id is “movie:3”.
 db.movie.updateOne({_id: “movie:3”, country: “USA” } {$set:{country: “FR”}}) 
5. Update the movie with director’s last_name is “Doe” from "Scott" where _id is "movie:9".
 db.movie.updateOne({_id: “movie:9” , “director.last_name”: “Scott” } {$set: {“ director.last_name”: “Doe”}})
6. Update the movie with director’s first_name “Olive” from “Bruce” where _id is "movie:12".
 db.movie.updateOne({_id: “movie:12”, “actors.first_name”: “Bruce”}, {$set: {“actors.$.first_name”: “Olive”}})
7. Update the movies with year 1990 where year is 1994.
 db.movie.updateMany({year: 1994},{$set:{year: 1990}})
8. Update the movies with country “USA” from "FR".
 db.movie.updateMany({country: “FR”}, {$set: {country: “USA”}})
9. Update the movies with genre “Drama” from “Action”.
 db.movie.updateMany({genre: “Action”}, {$set: {genre: “Drama”}}) 
10. Update the movies with director’s birth_date to 1990 where birth date older than 1980.
 db.movie.updateMany({“director.birth_date”: {$lt: Date(“190”)}}, {$set: {“directors.birth_date”: Date(“1990”)}})
========================================================================================================================================
C. Write the script to Search a string in the document on movie collection.
1. Fetch all the movies genre as “drama”.
 db.movie.find({genre: “drama”})
2. Fetch all the movies title with “Titanic”.
 db.movie.find({title: “Titanic”})
3. Fetch all the movies director’s first_name as “John”.
 db.movie.find({“director.first_name”: “john”})
4. Fetch all the movies title start with "G".
 db.movie.find({title: /^G/})
 
5. Fetch all the movies title end with "e".
 db.movie.find({title: /^e/})
 
6. Fetch all the movies title start and end with "t".
 db.movie.find({ title: /^t.*t$/i }, {title: 1})
7. find all movies that have a summary that contains the word "Los Angeles".
 db.movie.find({ summary: /Los Angeles/i }, {summary: 1})
8. find all movies that have a title that contains the word "Matrix".
 db.movie.find({ title: "Matrix"}, {title: 1})
9. find all movies that have a summary that contains the word "impossible".
 db.movie.find({ summary: { $regex: /impossible/i }} ,{summary: 1})
10. find all movies that have a summary that contains the word "Peter Parker".
 db.movies.find({ summary: { $regex: /Peter Parker/i } }, {summary: 1}) 
========================================================================================================================================
D. Write the script to create the indexes on movie collection.
1. Create an index on title attribute in ascending order on movie collection.
 db.movie.createIndex({ title: 1 })
2. Create a single index with multiple attributes (title by ascending order and genre by descending order) on movie.
 db.movie.createIndex({ title: 1, genre: -1 })
3. Create a single index with multiple attributes (title by descending order and country by ascending order) on movie.
 db.movie.createIndex({ title: -1, country: 1 })
4. Create multiple indexes based on the multiple attributes including composite index.
title: single index by ascending order
title and genre: composite index by descending order
year: single index by descending order
 db.movie.createIndex({ title: 1 })
 db.movie.createIndex({ title: -1, genre: -1 })
 db.movie.createIndex({ year: -1 })
5. Create a wildcard Index on director first_name order by ascending order on movie collection.
 db.movie.createIndex({ "director.first_name": 1 })
6. Create a unique index on country attribute by ascending order on movie collection.
 db.movie.createIndex({ country: 1 })
7. Create a multikey Index on actors first_name order by ascending order on movie collection.
 db.movie.createIndex({ "actors.first_name": 1 }, { multikey: true })
8. Get all the Indexes from movie collection.
 db.movie.showIndexes()
9. Remove “title” index from movie collection.
 movie.dropIndex("title_1") 
10. Drop all the indexes from movie collection.
 db.movie.dropIndexes()
========================================================================================================================================
E. Write the script to delete document on movie collection.
1. Delete the movie with title "Spider-Man".
 db.movie.deleteMany({ title: "Spider-Man" })
2. Delete the movies which is released in 1990.
 db.movie.deleteMany({ release_year: 1990 })
3. Delete the movies with director first_name is “Richard”.
 db.movie.deleteMany({ "director.first_name": "Richard" })
4. Delete a top movie released in USA.
 db.movie.deleteOne({ country: "USA" }, { sort: { rating: -1 }, limit: 1 })
5. Delete a movie with director birth_date is 1940.
 db.movie.deleteOne({ "director.birth_date": 1940 })
6. Delete the movies which is older than 1980.
 db.movie.deleteMany({“year”: { “$lt”: 1980}})
7. Delete the movie which is from country FR and year 1975.
 db.movie.deleteOne({“country”: “FR”, “year”: 1975})
8. Delete the movies with genre is drama.
 db.movie.deleteMany({“genre”: “drama”})
9. Delete the movies with year is 1990 and genre is Action.
 db.movie.deleteMany({“year”: 1990, “genre”: “action”})
10. Delete the movies with last_name “Burton”.
 db.movie.deleteMany({“director.last_name”: “Burton”})

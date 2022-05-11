SELECT mov_title, act_fname, act_lname, role
FROM movie 
JOIN movie_cast 
  ON movie_cast.mov_id=movie.mov_id 
JOIN actor 
  ON movie_cast.act_id=actor.act_id
WHERE actor.act_id IN (
SELECT act_id 
FROM movie_cast 
GROUP BY act_id HAVING COUNT(*)>=2);

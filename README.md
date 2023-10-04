# Netflix-And-Chill
-- Checking which movies are non english movies


SELECT *
FROM film f
JOIN language l
ON f.language_id = l.language_id
WHERE l.language_id >1 AND f.language_id IS NOT NULL
ORDER BY l.language_id DESC

-- Checking the average number of movies stars per movie


SELECT*
FROM film_actor fa
JOIN actor a
ON fa.actor_id = fa.actor_id
GROUP BY 2,1

-- As most of the data is spread across multiple tables I had to join all the dots


USE sakila;
SELECT
c.country,
ci.city,
f.title AS "Movie Title",
ct.name AS "Genre",
rating,
f.length AS "Movie Duration",
rental_rate AS "Rental Rate",
replacement_cost AS "Replacement Cost"
FROM country c
JOIN city ci
USING (country_id)
JOIN address ad
USING (city_id)
JOIN customer cs
USING (address_id)
JOIN rental r
USING (customer_id)
JOIN inventory i
USING (inventory_id)
JOIN film_category fc
ON i.film_id = fc.film_id
RIGHT JOIN category ct
ON fc.category_id = ct.category_id
JOIN film f
ON i.film_id = f.film_id
ORDER BY country 


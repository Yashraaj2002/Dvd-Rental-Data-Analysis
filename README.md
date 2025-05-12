# Dvd-Rental-Data-Analysis
Movie & Category Performance – SQL Analysis
This repository contains SQL queries and insights focused on analyzing movie performance and category trends in a DVD rental database.

Objectives
Identify top-performing movies

Analyze film category popularity and revenue

Derive business insights from rental data

Prepare data for visualizations in Power BI

SQL Queries & Insights
1. Top 10 Most-Rented Movies
SELECT 
    f.title,
    c.name AS category,
    COUNT(r.rental_id) AS movie_rental_count
FROM 
    film f
INNER JOIN 
    inventory i ON f.film_id = i.film_id
INNER JOIN 
    rental r ON i.inventory_id = r.inventory_id
INNER JOIN 
    film_category fc ON f.film_id = fc.film_id
INNER JOIN 
    category c ON fc.category_id = c.category_id  
GROUP BY 
    f.film_id, f.title, c.name
ORDER BY 
    movie_rental_count DESC
LIMIT 10;


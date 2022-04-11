# Elizabeth Figueroa's SQL Portfolio
## Welcome to my SQL Portfolio! This code repository contains examples of SQL I've written. Feel free to take a look and reach out via email you have any quesitons! 
elizabeth.figueroaef83@gmail.com

#1. How many movie titles are there in the database?
SELECT COUNT(*)
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
WHERE type='Movie';

#2. When was the most recent batch of tv shows and/or movies added to the database? 
SELECT MAX(date(date_added))
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info";

#3. List all the movies and tv shows in alphabetical order.
SELECT title
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
ORDER BY title ASC;

#4. Who was the Director for the movie Bright Star?
SELECT Director
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
LEFT JOIN  "CharlotteChaze/BreakIntoTech"."netflix_people" people
ON titles.show_id=people.show_id
WHERE titles.title='Bright Star'

#5. What is the oldest movie in the database and what year was it made? 
SELECT title, min(release_year) 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
WHERE type='Movie'
GROUP BY title, release_year
ORDER BY release_year ASC
LIMIT 1;

#6. How many orders were placed in January? 
SELECT COUNT(orderid)
FROM BIT_DB.JanSales

#7. How many of those orders were for an iPhone? 
SELECT COUNT(orderid)
FROM BIT_DB.JanSales
WHERE Product='iPhone'

#8. Select the customer account numbers for all the orders that were placed in February. 
SELECT acctnum
FROM BIT_DB.customers cust

INNER JOIN BIT_DB.FebSales Feb
ON cust.order_id=FEB.orderid

#9. Which product was the cheapest one sold in January, and what was the price? 
SELECT DISTINCT product, MIN(price) 
FROM BIT_DB.JanSales Jan 
GROUP BY product, price 
ORDER BY price ASC 
LIMIT 1

#10. What is the total revenue for each product sold in January?
SELECT SUM(quantity)*price as revenue, product
FROM BIT_DB.JanSales
GROUP BY product

#11. Which products were sold in February at 548 Lincoln St, Seattle, WA 98101, how many of each were sold, and what was the total revenue?
select 
sum(Quantity), 
product, 
sum(quantity)*price as revenue
FROM BIT_DB.FebSales 
WHERE location = '548 Lincoln St, Seattle, WA 98101'
GROUP BY product

#12. How many customers ordered more than 2 products at a time, and what was the average amount spent for those customers? 
select 
count(cust.acctnum), 
avg(quantity)*price
FROM BIT_DB.FebSales Feb
LEFT JOIN BIT_DB.customers cust
ON FEB.orderid=cust.order_id
WHERE Feb.Quantity>2

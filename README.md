# Odev12.sql

--1.film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

```
SELECT COUNT(title) from film
WHERE length >
(
	SELECT AVG(length) from film
);
```

--2.film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

```
SELECT COUNT(title) from film
WHERE rental_rate =
(
	SELECT MAX(rental_rate) from film
);
```

--3.film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

```
SELECT title from film
WHERE rental_rate = (SELECT MIN(rental_rate) from film) AND 
replacement_cost = (SELECT MIN(replacement_cost) from film);
```

--4.payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

```
SELECT first_name, last_name, customer.customer_id, COUNT(*) 
FROM payment
INNER JOIN customer ON payment.customer_id = customer.customer_id
GROUP BY customer.customer_id
ORDER BY COUNT(*) DESC
LIMIT 10;
```

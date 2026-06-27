# Домашнее задание к занятию «SQL. Часть 2»

**Выполнил:** Михаил Лукьянов

---

# Задание 1

## SQL-запрос

```sql
SELECT
    staff.first_name,
    staff.last_name,
    city.city,
    COUNT(customer.customer_id) AS customers
FROM store
JOIN staff
    ON store.manager_staff_id = staff.staff_id
JOIN address
    ON store.address_id = address.address_id
JOIN city
    ON address.city_id = city.city_id
JOIN customer
    ON store.store_id = customer.store_id
GROUP BY
    store.store_id,
    staff.first_name,
    staff.last_name,
    city.city
HAVING COUNT(customer.customer_id) > 300;
```

## Результат выполнения

<img width="2385" height="1195" alt="1" src="https://github.com/user-attachments/assets/84ab87cd-5ce3-4840-aec9-2cadf88ff3fb" />

---
# Задание 2

## SQL-запрос

```sql
SELECT COUNT(*)
FROM film
WHERE length > (
    SELECT AVG(length)
    FROM film
);
```

## Результат выполнения
 
 <img width="1487" height="625" alt="2" src="https://github.com/user-attachments/assets/b5fd8d9c-b2af-4404-b2bd-8f839774d538" />


# Задание 3

## SQL-запрос

```sql
SELECT
    MONTH(payment_date) AS month,
    SUM(amount) AS total_amount,
    COUNT(rental_id) AS rentals
FROM payment
GROUP BY MONTH(payment_date)
ORDER BY total_amount DESC
LIMIT 1;
```

## Результат выполнения

<img width="1422" height="682" alt="3" src="https://github.com/user-attachments/assets/ae322a1c-2d21-409f-bde9-26a370b7afc4" />


# Задание 4*

## SQL-запрос

```sql
SELECT
    staff.first_name,
    staff.last_name,
    COUNT(payment.payment_id) AS sales,
    CASE
        WHEN COUNT(payment.payment_id) > 8000 THEN 'YES'
        ELSE 'NO'
    END AS bonus
FROM staff
JOIN payment
    ON staff.staff_id = payment.staff_id
GROUP BY
    staff.staff_id,
    staff.first_name,
    staff.last_name;
```

## Результат выполнения

<img width="1605" height="1010" alt="4" src="https://github.com/user-attachments/assets/2ec675d2-4c64-45bc-b472-fef3379efada" />



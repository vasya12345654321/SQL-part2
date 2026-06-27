SQL-запрос
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

<img width="2385" height="1195" alt="1" src="https://github.com/user-attachments/assets/ce738cbe-40c1-4189-96ca-2dee9ae8783a" />

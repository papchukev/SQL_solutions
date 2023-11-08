![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/f35e4a3d-284f-4b04-81b4-e61e52e1ab5f)

------------
    SELECT customer_id
    FROM Customer
    GROUP BY customer_id
    HAVING COUNT(DISTINCT product_key) = (SELECT COUNT(product_key) FROM Product)

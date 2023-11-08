![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/5fd5cb27-6b95-43f5-b4cb-3133c16165f7)

----------------
    SELECT DISTINCT product_id, year AS first_year, quantity, price
    FROM Sales
    WHERE (product_id, year) IN(SELECT product_id, MIN(year) FROM Sales GROUP BY product_id)
    ;

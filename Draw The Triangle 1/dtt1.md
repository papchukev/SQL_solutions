![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/767de7de-faec-4795-8f16-e97923706d9d)

-----------------------
    WITH RECURSIVE cte AS(SELECT 20 AS n, CAST('*' AS CHAR(100)) AS str, 1 AS ID
                          UNION ALL
                          SELECT n - 1, concat('* ',str), ID + 1 
                          FROM cte 
                          WHERE n > 1)
    SELECT str FROM cte
    ORDER BY ID DESC
    ;

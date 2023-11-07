![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/a84c62a2-faca-4a52-929f-68135020637a)

--------
    WITH RECURSIVE CTE AS(SELECT 1 AS N, CAST('*' AS CHAR(100)) AS STR
                          UNION ALL
                          SELECT N + 1, CONCAT('* ', STR)
                          FROM CTE
                          WHERE N < 20)
    SELECT STR
    FROM CTE

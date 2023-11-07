![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/b295c89c-7c0b-4da8-8a74-4f6f7aadb01b)

---------------
    WITH RECURSIVE CTE AS(SELECT 1 AS N
                          UNION ALL
                          SELECT N + 1 AS ALL_NUMB
                          FROM CTE
                          WHERE N < 1000),
        TABLE_NUMB AS(SELECT N AS X
                      FROM CTE)
    
    SELECT GROUP_CONCAT(X SEPARATOR '&')
    FROM TABLE_NUMB
    WHERE NOT EXISTS(SELECT N FROM CTE WHERE N < X AND X % N = 0 AND N > 1) AND X > 1
    ;

![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/329fc0a5-4067-4462-9f83-6cc1c1c9d4b7)

-----------------
    WITH IDTAB AS(SELECT X, Y,
                  ROW_NUMBER() OVER() AS ID
                  FROM Functions),
    TAB_TAB AS (SELECT T1.X AS TABX, T1.Y AS TABY, T2.X AS TAB2X, T2.Y, CAST(T1.ID AS SIGNED), CAST(T2.ID AS SIGNED)
                FROM IDTAB T1
                JOIN IDTAB T2 ON T2.Y = T1.X AND T2.X = T1.Y
                WHERE T2.ID <> T1.ID AND T1.X <= T1.Y
                ORDER BY T1.X)
    
    SELECT DISTINCT TABX, TABY
    FROM TAB_TAB
    ORDER BY TABX
    ;

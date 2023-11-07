![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/6154ddfd-58b6-4057-8e3d-7296f1bd6449)

----------------
    WITH TAB1 AS(SELECT 
                    TASK_ID, 
                    START_DATE, 
                    END_DATE, 
                    START_DATE - ROW_NUMBER() OVER(ORDER BY START_DATE) AS GRP
                FROM PROJECTS)
    
    SELECT MIN(START_DATE) AS ST, MAX(END_DATE) AS EN
    FROM TAB1
    GROUP BY GRP
    ORDER BY (EN - ST)
    ;

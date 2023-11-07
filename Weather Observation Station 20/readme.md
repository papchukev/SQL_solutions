![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/9acc31ae-976e-480c-a5d0-a3cb5a493e38)

-------------------
    WITH RANKED AS(SELECT LAT_N , RANK() OVER (ORDER BY LAT_N) AS RANG 
                   FROM STATION)
    SELECT CASE 
        WHEN COUNT(LAT_N) % 2 <> 0 THEN (SELECT ROUND(LAT_N, 4) 
                                         FROM RANKED 
                                         WHERE RANG = (SELECT (COUNT(ID) + 1) / 2 FROM STATION))  
        WHEN COUNT(LAT_N) % 2 = 0 THEN (SELECT ROUND(LAT_N, 4) 
                                        FROM RANKED 
                                        WHERE RANG = (SELECT COUNT(ID) / 2 FROM STATION)) + (SELECT ROUND(LAT_N, 4) 
                                                                                             FROM RANKED 
                                                                                             WHERE RANG = (SELECT (COUNT(ID) + 1) / 2 FROM STATION)) / 2
        END
    FROM RANKED

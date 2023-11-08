![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/06633644-0652-464d-a85c-5c724462ba15)

----------------
    SELECT MAX(mnum) AS num
    FROM (SELECT num AS mnum 
          FROM MyNumbers 
          GROUP BY num 
          HAVING COUNT(num) = 1) nu

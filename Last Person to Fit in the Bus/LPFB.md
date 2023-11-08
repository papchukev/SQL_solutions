![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/b3dccd71-2876-47a8-9864-f538147f8459)

----------------
    WITH tab1 AS(SELECT 
                    turn, 
                    person_id, 
                    person_name, 
                    weight,
                    SUM(weight) OVER(ORDER BY turn) AS total_weight
                 FROM Queue)
    SELECT person_name
    FROM tab1
    WHERE total_weight <= 1000 AND turn = (SELECT MAX(turn) FROM tab1 WHERE total_weight <= 1000)
    ;

![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/978b1cfd-332f-43d6-84a1-c3ddc5388798)

---------------
    SELECT ROUND(COUNT(DISTINCT a2.player_id) / COUNT(DISTINCT a1.player_id), 2) AS fraction
    FROM Activity a1
    LEFT JOIN Activity a2
      ON a2.player_id = a1.player_id
      AND a2.event_date = a1.event_date + interval 1 day
      AND (a1.player_id, a1.event_date) IN(SELECT player_id, MIN(event_date) FROM Activity GROUP BY player_id)
    ;

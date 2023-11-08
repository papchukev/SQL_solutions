![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/d5d179c5-9e7a-4e92-ba2a-5103f4bc56e9)

----------------------
    SELECT s.user_id, ROUND(AVG(CASE 
                                    WHEN c2.action = 'confirmed' THEN 1
                                    ELSE 0
                                END), 2) AS confirmation_rate
    FROM Signups s
    LEFT JOIN Confirmations c2 ON c2.user_id = s.user_id
    GROUP BY s.user_id
    ;

![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/b3e6df96-17a9-496e-a206-1726a4989954)

-------
    SELECT e1.name
    FROM employee e1
    JOIN employee e2 ON e2.managerId = e1.id
    GROUP BY e1.id
    HAVING COUNT(e2.managerId) >= 5

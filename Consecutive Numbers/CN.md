![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/edb5e007-4483-4fd4-9e07-c047c325827e)

-----------
    SELECT DISTINCT l1.num AS ConsecutiveNums
    FROM Logs l1
    JOIN logs l2 ON l1.num = l2.num AND l2.id = l1.id + 1
    JOIN logs l3 ON l1.num = l3.num AND l3.id = l2.id + 1

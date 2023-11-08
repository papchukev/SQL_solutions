![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/0da03718-30af-4243-9b91-0c214672aa37)

-------------
    SELECT x, y, z, IF(x < y + z AND y < x + z AND z < x + y, 'Yes', 'No') AS triangle
    FROM Triangle

![btn](https://github.com/papchukev/SQL_solutions/assets/149643273/3b95f45c-0ad1-4f63-b10c-8140fabec7cf)

    SELECT N, 
        CASE
            WHEN ISNULL(P) THEN 'Root'
            WHEN N IN(SELECT DISTINCT P FROM BST B1) THEN 'Inner'
            ELSE 'Leaf'        
            END
    FROM BST
    ORDER BY N

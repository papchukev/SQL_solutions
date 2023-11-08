![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/91ff117e-14d6-4aef-a0a1-f56c8a71d7fd)

--------------------
    SELECT "Low Salary" AS category, COUNT(account_id) AS accounts_count
    FROM Accounts
    WHERE income < 20000
    UNION 
    SELECT "Average Salary" AS category, COUNT(account_id) AS accounts_count
    FROM Accounts
    WHERE income BETWEEN 20000 AND 50000
    UNION
    SELECT "High Salary" AS category, COUNT(account_id) AS accounts_count
    FROM Accounts
    WHERE income > 50000
    ;

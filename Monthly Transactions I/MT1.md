![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/f0c8d544-36fa-44c0-91a3-5144174af4c5)

-----------
    SELECT DATE_FORMAT(t1.trans_date, '%Y-%m') AS month,
           t1.country,
           COUNT(t1.id) AS trans_count,
           COUNT(t2.id) AS approved_count,
           COALESCE(SUM(t1.amount), 0) AS trans_total_amount,
           COALESCE(SUM(t2.amount), 0) AS approved_total_amount
    FROM Transactions t1
    LEFT JOIN Transactions t2
      ON t2.id = t1.id
      AND t2.country = t1.country
      AND t2.amount = t1.amount
      AND t2.trans_date = t1.trans_date
      AND t2.state like 'approved'
    GROUP BY month, t1.country

![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/fc714fd7-b201-4412-b83f-a27b5c1defca)

-----------
    SELECT ROUND(COUNT(DISTINCT d2.customer_id) / COUNT(DISTINCT d1.customer_id) * 100, 2) AS immediate_percentage
    FROM Delivery d1
    LEFT JOIN Delivery d2
      ON d2.customer_id = d1.customer_id
      AND d2.delivery_id = d1.delivery_id
      AND d2.customer_pref_delivery_date = d1.order_date
      AND (d2.customer_id, d2.order_date) IN(SELECT customer_id, MIN(order_date) FROM Delivery GROUP BY customer_id)
    ;

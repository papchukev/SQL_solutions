![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/84dd74f4-5443-46ad-8d68-8b00e5c5b714)

-------------------
    WITH part1 AS(SELECT 
                    submission_date, 
                    hacker_id , 
                    ct1,
                    ROW_NUMBER() OVER(PARTITION BY submission_date ORDER BY ct1 DESC, hacker_id) AS rnum 
                  FROM (SELECT submission_date, hacker_id, COUNT(submission_id) AS ct1
                        FROM submissions
                        GROUP BY submission_date, hacker_id) source1
                  WHERE ct1 > 0),
    
    part2 AS(SELECT submission_date, COUNT(hacker_id) AS ct2 
             FROM (SELECT submission_date, hacker_id, ROW_NUMBER() OVER(PARTITION BY hacker_id ORDER BY submission_date) AS rday
                   FROM part1) source2
             WHERE rday = DAY(submission_date)
             GROUP BY submission_date)
    
    SELECT part1.submission_date, part2.ct2, part1.hacker_id, h.name
    FROM part1
    JOIN part2 ON part1.submission_date = part2.submission_date
    LEFT JOIN hackers h ON part1.hacker_id = h.hacker_id
    WHERE part1.rnum = 1
    ORDER BY submission_date
    ;

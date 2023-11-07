![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/f99ddec1-9639-4a76-b9a6-71c7e4e34376)

----------------------------
    SELECT 
        CONT.contest_id, 
        CONT.hacker_id, 
        CONT.name, 
        TS.sum_of_total_submissions, 
        TS.sum_of_total_accepted_submissions,
        TV.sum_of_total_views, 
        TV.sum_of_total_unique_views 
    FROM Contests CONT 
    INNER JOIN (SELECT COLL.contest_id, 
                       SUM(SS.total_submissions) AS sum_of_total_submissions, 
                       SUM(SS.total_accepted_submissions) AS sum_of_total_accepted_submissions
                FROM Colleges COLL 
                INNER JOIN Challenges CHALL 
                ON CHALL.college_id = COLL.college_id 
                INNER JOIN submission_stats SS 
                ON SS.challenge_id = CHALL.challenge_id 
                GROUP BY COLL.contest_id) TS 
    ON TS.contest_id = CONT.contest_id 
    
    INNER JOIN (SELECT COLL.contest_id, 
                       SUM(VS.total_views) AS sum_of_total_views, 
                       SUM(VS.total_unique_views) AS sum_of_total_unique_views
                FROM Colleges COLL 
                INNER JOIN Challenges CHALL 
                ON CHALL.college_id = COLL.college_id 
                INNER JOIN view_stats VS 
                ON VS.challenge_id = CHALL.challenge_id 
                GROUP BY COLL.contest_id) TV 
    ON TV.contest_id = CONT.contest_id 
   
    WHERE TS.sum_of_total_submissions > 0 
      OR TS.sum_of_total_accepted_submissions > 0 
      OR TV.sum_of_total_views > 0 
      OR TV.sum_of_total_unique_views > 0 
    ORDER BY CONT.contest_id
    ;

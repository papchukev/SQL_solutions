![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/9664436d-85ee-4525-80b3-2e3cdaf5fb02)

---------------------
    WITH CHALLENGE_COUNT AS(SELECT HACKERS.HACKER_ID, NAME, COUNT(CHALLENGE_ID) AS CHALL
                            FROM HACKERS 
                            JOIN CHALLENGES 
                            ON CHALLENGES.HACKER_ID = HACKERS.HACKER_ID
                            GROUP BY NAME, HACKERS.HACKER_ID
                            ORDER BY CHALL DESC),
    
    MAX_CHAL AS(SELECT MAX(CHALLENGE_COUNT.CHALL) 
                FROM CHALLENGE_COUNT),
    
    TOTAL_CHAL AS(SELECT CHALL, COUNT(CHALL)
                  FROM CHALLENGE_COUNT
                  GROUP BY CHALL
                  HAVING COUNT(CHALL) = 1 OR 
                  CHALL = (SELECT * FROM MAX_CHAL))
    
    SELECT  HACKER_ID, NAME, CHALLENGE_COUNT.CHALL
    FROM CHALLENGE_COUNT
    JOIN TOTAL_CHAL ON TOTAL_CHAL.CHALL = CHALLENGE_COUNT.CHALL
    ORDER BY CHALLENGE_COUNT.CHALL DESC, HACKER_ID
    ;

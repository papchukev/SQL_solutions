![изображение](https://github.com/papchukev/SQL_solutions/assets/149643273/0cca5271-10fe-4fef-b757-7002a2c994f2)

------------------
    WITH SALARY_TAB AS(SELECT 
                          S1.NAME, 
                          P1.SALARY AS STUD_SALARY,         
                          FRIENDS.ID,
                          P2.SALARY AS FRIEND_SALARY
                       FROM STUDENTS S1
                       JOIN PACKAGES P1 ON P1.ID = S1.ID
                       JOIN FRIENDS ON FRIENDS.ID = S1.ID
                       JOIN PACKAGES P2 ON P2.ID = FRIENDS.FRIEND_ID)
    
    SELECT NAME
    FROM SALARY_TAB
    WHERE FRIEND_SALARY > STUD_SALARY
    ORDER BY FRIEND_SALARY
    ;

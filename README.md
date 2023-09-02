# SQL-Practice
Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.
SELECT
    HK.HACKER_ID
    ,HK.NAME
FROM 
    SUBMISSIONS SUB, CHALLENGES CHA, DIFFICULTY DF, HACKERS HK
WHERE
    SUB.CHALLENGES_ID = CHA.CHALLENGES_ID
    AND CHA.DIFFICULTY_LEVEL = DF.DIFFICULTY_LEVEL
    AND SUB.SCORE = DF.SCORE
    AND HK.HACKER_ID = SUB.HACKER_ID
GROUP BY 
    HK.HACKER_ID, HK.NAME
HAVING 
    COUNT(HK.NAME) > 1
ORDER BY
    COUNT(HK.NAME) DESC,
    HK.HACKER_ID ASC

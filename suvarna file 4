-- Student Result Management System: Queries

-- 1. Topper in DBMS
SELECT s.StudentID, s.Name, m.Marks
FROM Students s
JOIN Marks m ON s.StudentID = m.StudentID
JOIN Subjects sub ON m.SubjectID = sub.SubjectID
WHERE sub.SubjectName = 'DBMS'
  AND m.Marks = (
      SELECT MAX(m2.Marks)
      FROM Marks m2
      JOIN Subjects sub2 ON m2.SubjectID = sub2.SubjectID
      WHERE sub2.SubjectName = 'DBMS'
  );

-- 2. Students scoring above 80 in all their subjects
SELECT s.StudentID, s.Name
FROM Students s
JOIN Marks m ON s.StudentID = m.StudentID
GROUP BY s.StudentID, s.Name
HAVING MIN(m.Marks) > 80;

-- 3. Average marks of each subject
SELECT sub.SubjectID, sub.SubjectName, ROUND(AVG(m.Marks), 2) AS AvgMarks
FROM Subjects sub
JOIN Marks m ON sub.SubjectID = m.SubjectID
GROUP BY sub.SubjectID, sub.SubjectName;

-- 4. Students who failed (pass mark assumed = 40; fails if below 40 in any subject)
SELECT DISTINCT s.StudentID, s.Name
FROM Students s
JOIN Marks m ON s.StudentID = m.StudentID
WHERE m.Marks < 40;

-- 5. CGPA (credit-weighted; 90+=10, 80+=9, 70+=8, 60+=7, 50+=6, 40+=5, else 0)
SELECT s.StudentID, s.Name,
       ROUND(
         SUM(
           CASE
             WHEN m.Marks >= 90 THEN 10
             WHEN m.Marks >= 80 THEN 9
             WHEN m.Marks >= 70 THEN 8
             WHEN m.Marks >= 60 THEN 7
             WHEN m.Marks >= 50 THEN 6
             WHEN m.Marks >= 40 THEN 5
             ELSE 0
           END * sub.Credits
         ) / SUM(sub.Credits), 2
       ) AS CGPA
FROM Students s
JOIN Marks m ON s.StudentID = m.StudentID
JOIN Subjects sub ON m.SubjectID = sub.SubjectID
GROUP BY s.StudentID, s.Name;

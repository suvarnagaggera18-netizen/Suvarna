-- Library Management System: Queries (MySQL syntax)

-- 1. Overdue books (loan period assumed = 14 days)
--    Overdue = not returned after 14 days, or returned after the due date
SELECT i.IssueID, b.BookName, m.Name AS Member, i.IssueDate,
       DATE_ADD(i.IssueDate, INTERVAL 14 DAY) AS DueDate
FROM Issue i
JOIN Books b   ON i.BookID = b.BookID
JOIN Members m ON i.MemberID = m.MemberID
WHERE (i.ReturnDate IS NULL AND CURDATE() > DATE_ADD(i.IssueDate, INTERVAL 14 DAY))
   OR (i.ReturnDate > DATE_ADD(i.IssueDate, INTERVAL 14 DAY));

-- 2. Books never issued
SELECT b.BookID, b.BookName, b.Author
FROM Books b
LEFT JOIN Issue i ON b.BookID = i.BookID
WHERE i.IssueID IS NULL;

-- 3. Member who borrowed the maximum number of books
SELECT m.MemberID, m.Name, COUNT(*) AS BooksBorrowed
FROM Members m
JOIN Issue i ON m.MemberID = i.MemberID
GROUP BY m.MemberID, m.Name
HAVING COUNT(*) = (
    SELECT MAX(cnt)
    FROM (SELECT COUNT(*) AS cnt FROM Issue GROUP BY MemberID) t
);

-- 4. Most popular book (issued the most times)
SELECT b.BookID, b.BookName, COUNT(*) AS TimesIssued
FROM Books b
JOIN Issue i ON b.BookID = i.BookID
GROUP BY b.BookID, b.BookName
HAVING COUNT(*) = (
    SELECT MAX(cnt)
    FROM (SELECT COUNT(*) AS cnt FROM Issue GROUP BY BookID) t
);

-- 5. Count of available books (not currently issued, i.e. no unreturned copy)
SELECT COUNT(*) AS AvailableBooks
FROM Books b
WHERE b.BookID NOT IN (
    SELECT BookID FROM Issue WHERE ReturnDate IS NULL
);

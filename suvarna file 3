-- Library Management System: Table Creation

CREATE TABLE Books (
    BookID   VARCHAR(10) PRIMARY KEY,
    BookName VARCHAR(100) NOT NULL,
    Author   VARCHAR(100) NOT NULL
);

CREATE TABLE Members (
    MemberID   INT PRIMARY KEY,
    Name       VARCHAR(50) NOT NULL,
    Department VARCHAR(10) NOT NULL
);

CREATE TABLE Issue (
    IssueID    INT PRIMARY KEY,
    BookID     VARCHAR(10) NOT NULL,
    MemberID   INT NOT NULL,
    IssueDate  DATE NOT NULL,
    ReturnDate DATE NULL,
    FOREIGN KEY (BookID) REFERENCES Books(BookID),
    FOREIGN KEY (MemberID) REFERENCES Members(MemberID)
);

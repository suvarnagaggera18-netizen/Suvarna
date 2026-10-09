-- Student Result Management System: Table Creation

CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name      VARCHAR(50) NOT NULL,
    Branch    VARCHAR(10) NOT NULL,
    Year      INT NOT NULL
);

CREATE TABLE Subjects (
    SubjectID   VARCHAR(10) PRIMARY KEY,
    SubjectName VARCHAR(50) NOT NULL,
    Credits     INT NOT NULL
);

CREATE TABLE Marks (
    StudentID INT,
    SubjectID VARCHAR(10),
    Marks     INT CHECK (Marks BETWEEN 0 AND 100),
    PRIMARY KEY (StudentID, SubjectID),
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (SubjectID) REFERENCES Subjects(SubjectID)
);

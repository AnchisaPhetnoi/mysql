CREATE DATABASE SchoolDB;
USE SchoolDB;

CREATE TABLE Major (
    MajorID INT AUTO_INCREMENT PRIMARY KEY,   -- รหัสวิชาเอก ใช้เป็น Primary Key และเพิ่มอัตโนมัติ
    MajorName VARCHAR(255) NOT NULL,          -- ชื่อวิชาเอก
    Location VARCHAR(255)                     -- สถานที่เรียน
);

CREATE TABLE Student (
    SID INT AUTO_INCREMENT PRIMARY KEY,       -- รหัสนักเรียน Primary Key และเพิ่มอัตโนมัติ
    Sname VARCHAR(255) NOT NULL,              -- ชื่อนักเรียน ห้ามเว้นว่าง
    GPA DECIMAL(3,2),                         -- เกรดเฉลี่ยสะสมในรูปแบบทศนิยม
    MajorID INT,                              -- รหัสวิชาเอก ที่เชื่อมโยงกับตาราง Major
    FOREIGN KEY (MajorID) REFERENCES Major(MajorID)  -- เชื่อมโยง MajorID กับ Major
);


CREATE TABLE Course (
    CID INT AUTO_INCREMENT PRIMARY KEY,       -- รหัสวิชา Primary Key และเพิ่มอัตโนมัติ
    Cname VARCHAR(255) NOT NULL               -- ชื่อวิชา
);

CREATE TABLE Registration (
    RID INT AUTO_INCREMENT PRIMARY KEY,       -- รหัสการลงทะเบียน
    SID INT NOT NULL,                         -- รหัสนักเรียน (ต้องไม่เป็นค่าว่าง)
    Semester VARCHAR(10) NOT NULL,            -- ภาคการศึกษา
    FOREIGN KEY (SID) REFERENCES Student(SID) -- เชื่อมโยงกับรหัสนักเรียนในตาราง Student
);

CREATE TABLE RegDetail (
    RID INT,                                  -- รหัสการลงทะเบียน
    CID INT,                                  -- รหัสวิชา
    PRIMARY KEY (RID, CID),                   -- ใช้คู่ RID และ CID เป็น Primary Key
    FOREIGN KEY (RID) REFERENCES Registration(RID),  -- เชื่อมโยงกับตาราง Registration
    FOREIGN KEY (CID) REFERENCES Course(CID)         -- เชื่อมโยงกับตาราง Course
);


INSERT INTO Major (MajorName, Location)
VALUES ('Computer Science', 'Building A'),
       ('Electrical Engineering', 'Building B');
       
       
 INSERT INTO Student (Sname, GPA, MajorID)
VALUES ('Jon bye', 3.5, 1), ('Anchisa', 3.8, 2);

INSERT INTO Course (Cname)
VALUES ('Database Systems'), ('Operating Systems');

INSERT INTO Registration (SID, Semester)
VALUES (1, '2024-1'), (2, '2024-2');

INSERT INTO RegDetail (RID, CID)
VALUES (1, 1), (2, 2);

SELECT * FROM Student;      
       
       
       
       
       
       
       
       
       
       


# Database Documentation

## Overview

The current project is a static educational website.

For production deployment, a MySQL database should be implemented to manage students, courses, admissions, instructors, and inquiries.

Database Name:

career_ws_db

---

# Entity Relationship Diagram

Students
│
├── Enrollments
│
├── Payments
│
└── Certificates

Courses
│
├── Enrollments
│
└── Instructors

---

# Tables

## students

Stores student information.

Fields:

id

full_name

email

phone

password

created_at

---

## courses

Stores available courses.

Fields:

id

course_name

description

duration

fee

image

status

created_at

---

## instructors

Stores instructor information.

Fields:

id

name

email

phone

specialization

created_at

---

## enrollments

Stores student course registrations.

Fields:

id

student_id

course_id

enrollment_date

status

created_at

---

## payments

Stores fee payments.

Fields:

id

student_id

amount

payment_method

payment_status

created_at

---

## certificates

Stores issued certificates.

Fields:

id

student_id

course_id

certificate_number

issue_date

created_at

---

## contact_messages

Stores inquiries.

Fields:

id

name

email

subject

message

created_at

---

# Security Recommendations

bcrypt Password Hashing

Prepared Statements

Input Validation

Role-Based Access Control

Audit Logging

---

# Future Scaling

Learning Management System

Online Exams

Assignments

Student Portal

Video Lectures

Mobile Application


CREATE DATABASE career_ws_db;
USE career_ws_db;

CREATE TABLE students (
id INT AUTO_INCREMENT PRIMARY KEY,
full_name VARCHAR(150) NOT NULL,
email VARCHAR(150) UNIQUE NOT NULL,
phone VARCHAR(20),
password VARCHAR(255) NOT NULL,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE instructors (
id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(150) NOT NULL,
email VARCHAR(150),
phone VARCHAR(20),
specialization VARCHAR(150),
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE courses (
id INT AUTO_INCREMENT PRIMARY KEY,
course_name VARCHAR(255) NOT NULL,
description TEXT,
duration VARCHAR(100),
fee DECIMAL(10,2),
image VARCHAR(255),
status ENUM('active','inactive') DEFAULT 'active',
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE enrollments (
id INT AUTO_INCREMENT PRIMARY KEY,
student_id INT NOT NULL,
course_id INT NOT NULL,
enrollment_date DATE,
status ENUM('pending','approved','completed') DEFAULT 'pending',
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
FOREIGN KEY (student_id) REFERENCES students(id),
FOREIGN KEY (course_id) REFERENCES courses(id)
);

CREATE TABLE payments (
id INT AUTO_INCREMENT PRIMARY KEY,
student_id INT NOT NULL,
amount DECIMAL(10,2),
payment_method VARCHAR(50),
payment_status ENUM('pending','paid','failed') DEFAULT 'pending',
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
FOREIGN KEY (student_id) REFERENCES students(id)
);

CREATE TABLE certificates (
id INT AUTO_INCREMENT PRIMARY KEY,
student_id INT NOT NULL,
course_id INT NOT NULL,
certificate_number VARCHAR(100) UNIQUE,
issue_date DATE,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
FOREIGN KEY (student_id) REFERENCES students(id),
FOREIGN KEY (course_id) REFERENCES courses(id)
);

CREATE TABLE contact_messages (
id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(150),
email VARCHAR(150),
subject VARCHAR(255),
message TEXT,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


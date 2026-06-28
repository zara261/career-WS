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

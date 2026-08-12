BKOS FRONTEND ROUTES

VERSION

1.0

==================================================

ROUTE

/

PAGE

Welcome Page

PURPOSE

Landing page for visitors.

FEATURES

Platform Overview
Login Button
Register Button

==================================================

ROUTE

/register

PAGE

Registration Page

PURPOSE

Create new student account.

FEATURES

Name
Email
Mobile Number
Password
Language Selection

==================================================

ROUTE

/login

PAGE

Login Page

PURPOSE

Authenticate user.

FEATURES

Email Login
Mobile Login
Password Reset

==================================================

ROUTE

/dashboard

PAGE

Dashboard

PURPOSE

Main user workspace.

FEATURES

Continue Learning
My Subjects
Recent Activity
Progress Summary
Revision Alerts

==================================================

ROUTE

/subjects

PAGE

Subjects

PURPOSE

Display all available subjects.

FEATURES

Physics
Chemistry
Mathematics
Biology
English

==================================================

ROUTE

/subjects/{subject_id}/chapters

PAGE

Chapters

PURPOSE

Display chapters of selected subject.

FEATURES

Chapter List
Progress Status
Chapter Search

==================================================

ROUTE

/chapters/{chapter_id}/topics

PAGE

Topics

PURPOSE

Display topics under chapter.

FEATURES

Topic List
Difficulty Level
Completion Status

==================================================

ROUTE

/topics/{topic_id}/questions

PAGE

Questions

PURPOSE

Practice questions for topic.

FEATURES

MCQ
Confidence Selection
Timer
Submit Answer

==================================================

ROUTE

/results

PAGE

Results

PURPOSE

Show performance report.

FEATURES

Score
Accuracy
Confidence Analysis
Time Analysis

==================================================

ROUTE

/mistakes

PAGE

Mistake Review

PURPOSE

Display incorrect answers.

FEATURES

Wrong Questions
Weak Concepts
Recommended Revision

==================================================

ROUTE

/revision

PAGE

Revision Center

PURPOSE

Manage scheduled revisions.

FEATURES

Day 1 Revision
Day 7 Revision
Day 15 Revision
Day 30 Revision
Day 90 Revision

==================================================

ROUTE

/profile

PAGE

Profile

PURPOSE

Manage account settings.

FEATURES

Personal Information
Language
Preferences
Account Settings

==================================================

BKOS ROUTE FLOW

Welcome
↓
Register/Login
↓
Dashboard
↓
Subjects
↓
Chapters
↓
Topics
↓
Questions
↓
Results
↓
Mistakes
↓
Revision
↓
Mastery

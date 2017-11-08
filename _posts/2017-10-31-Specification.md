---
layout: post
title:  Specification
date:   2017-10-31 16:00:00 +0800
categories: document
tag: Spec
---

* content
{:toc}


## Introduction

### 1.Project Identification


### 2.Purpose

- This Software Requirement Specification (SRS) identifies the requirements and specification for the software of this project. It explains the functional features of the animation together with design, interface details and other considerations.

### 3.Scope

 

### 4.Overview

- The rest of the SRS presents the specifications of the software in detail. Section 2 of the SRS is the overall descriptions of the software and its functional requirements. Section 3 outlines other related non-functional requirements of the software.

 

## Overall Descriptions

- This section specifies the software platform and functional requirements including core features and optional features.

 

### 1.Product Perspectives

- The software is a web based product intended for use on Linux and mobile phone.

 

### 2.Product Functions

- The list provides a description of main functional features. These features are divided to two categories: core features and optional features. Core features are essential to the operation of the application, and optional features are additional functionalities.

#### 1.Core features

##### 1.Conceptual Entities

###### 1.Module

- A module represents a course in the university.

1. Module information

- A module contains a name, a code, an academic year, one or more module conveners, zero or more teaching assistants, and a student list.

2. Module creation

- A module must created by an administrator. The name, code, and academic year are required to create a module.

3. Updating module information

- After the creation, an administrator may modify the information of the module, such as assigning module convenors. (Who will assign the teaching assistants?)[meeting required]

4. Student list

- The student list is a set of student records, including all students once enrolled in the module, with an indicator of the enrollment status, which can be enrolled or exited. Each student record contains a student ID, a first name, a family name, a degree name, a gender, and an email address. The student records belong to the student list. If queries on a particular student involved in multiple modules is needed, the student is uniquely identified by the student ID.

- Any convenor of the module, or administrator, may edit the student list. The student list may be imported from a csv file, ("data source"), or manually edited.

- The system should provide a mechanism for adapting to differently formatted data source.

- The student records imported from the file should be merged with the existing information. Before the imported data affect the system, a detailed list of affected student records, including newly enrolled students, students present in the system but not in the data source, students in both the system and the data source, but their information conflicts, should be provided to the user.

- A student may be added to or removed from the student list, or marked as exited with an exit date. The removal function is only for removing incorrect information from the list, and should issue a warning before proceed.

5. Module archive

- When a module is finished, an administrator may archive the module, hereafter no information of the module may be changed, and no session of the module may be created, until the module is unarchived.

###### 2.Session

- A session belongs to a module. It represents a particular event of a module that requires an attendance record.

1. Session information

- A session contains a reference to its module, a time, a place, an attendance record, and optionally a type which can be lab, lecture, or customized text.

2. Creating a session

- A session can be manually created as needed, and removed if its attendance record is not created. Alternatively, a series of session repeating by weeks can be created by specifying the time of first session and a repeat count. Once created, all sessions are independent.

3. Starting a session

- Before a session starts, the module convenor should start the session manually to create its attendance record, which will be identical to the student list at that time. Then, the module convenor, or any lab assistant assigned to the module, may obtain a printable document of an attendance sheet containing a list of student ID, student name and signature area. That document may be obtained as many times as needed.

4. Attendance record

- The students in the attendance record can be added or removed by the module convenor.

5. Recording attendance

- A module convenor or teaching assistant can mark students absent in the attendance record. The module convenor can archive the session so the attendance record cannot be modified until it is unarchived. A senior tutor may attach an absent form series to a student in the attendance record in spite of the current state of the session.

###### 3.Absent form series

- An absent form series is a sequence of briefs of the absent form applications involved in an occasion of absence. Each brief contains a student name, a date, a module, a responsible user, a comment, and an approval status which may be approved, rejected, or undecided. The series is independent of attendance records, but may be referenced by it.

1. Creation

- An absent form series must be created by a senior tutor. 

2. Information control

- The contents of the forms are secured offline. The system only tracks the existance and status of the forms, any handling of the actual forms are performed outside the system.

- The comments can only be accessed by the responsible senior tutor.

3. Role

- Access to data is control by assigning permissions to objects to allow particular roles to access it, and assigning roles to users. For example, the convenors of a module forms a role, and the module object allows that role to read and write to it.

- An object can have zero or more permissions, and a user can have zero or more roles.

- Users are created by the administrator (integrate with LDAP if possible).

##### 2.Functional components
###### 1.Query

- Users may make queries on the attendance records if they have sufficient permissions.

- Several comment queries should be provided with shortcuts:

1. Absences by module
2. Absences by student
3. Absences by week
4. Absences by date range

- Users should also be able to make advanced queries on absence records by providing at least one of the following criteria:

1. Module convenor (inclusive/exclusive)
2. Module (inclusive/exclusive)
3. Student [id, gender, degree] (inclusive/exclusive)
4. Time (inclusive range, exclusive range)


#### Summarized permissions

- A = administrator
- S = senior tutor
- C = module convenor
- T = teaching assistant

##### All modules
1. create a module
2. archive a module
##### Managed module
1. view basic info
2. edit basic info
3. view student list
4. edit student list
##### attendance sheet

##### Senior Tutor: 

1. The system should allow senior tutor to create a module.
2. The system should allow senior tutor to block a achieved module. 
3. The system should allow senior tutor to check attendance rate of all modules and all students by day, week or month.
4. The system should allow senior tutor to search attendance record of a module by module name or code.
5. The system should allow senior tutor to search attendance record of a student by student name or ID.
6. The system should allow senior tutor to see EC application and the details about who, when and why.
7. The system should allow senior tutor to approval or reject EC form.

##### Module Convenor: 

1. The system should allow module convenor to create a class by DD/MM/YYYY.
2. The system should allow module convenor to assign lab assistances.
3. The system should allow module convenor to check attendance rate of this module and all enrolled student by day, week or month.
4. The system should allow module convenor to see the accepted EC form and the name of applicant.
5. The system should allow module convenor to add students that they are not on the enrolled student list.
6. The system should allow module convenor to sign attendees in student list.
7. The system should allow module convenor to download copy of currently enrolled student list.

##### Lab assistance:

1. The system should allow module convenor to download copy of currently enrolled student list.
2. The system should allow module convenor to sign attendees in student list.


#### Optional features


### 3.Specific Requirements

- This section specifies the nonfunctionalrequirements including capacity, software language, and online user documentation and help system requirements. 

1. Capacity

2. Software Language

3. Online User Documentation and Help System Requirements
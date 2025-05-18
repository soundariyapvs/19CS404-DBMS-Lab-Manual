# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints. 

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Royce Niran George A

## Scenario Chosen:
University

## ER Diagram:
![Screenshot 2025-04-30 215030](https://github.com/user-attachments/assets/f1020dca-2f30-4690-b95e-5426b6241490)


## Entities and Attributes:
->University

Attributes: uni_id, uni_name, location

->Department

Attributes: dept_id (PK), dept_name, uni_id (FK)

->Program

Attributes: prog_id (PK), prog_name, dept_id (FK)

->Faculty

Attributes: uni_id (FK)

->Course

Attributes: course_no (PK), course_name, credits

->Student

Attributes: reg_no (PK), name, DOB, ph_no, email

->Enrollment

Attributes: reg_no (FK), course_no (FK), date

## Relationships and Constraints:

$University — has → Department

Cardinality: 1:N (One university has many departments)

Participation: Total on department, partial on university


$Department — offers → Program

Cardinality: 1:N

Participation: Total on program


$Department — offers → Course

Cardinality: 1:N

Participation: Total on course


$Department — includes → Faculty

Cardinality: 1:N

Participation: Partial on faculty



$Student — enrolls in → Course (via Enrollment)

Cardinality: M:N (resolved using Enrollment table)

Participation: Partial on both

## Extension (Prerequisite / Billing):
Prerequisite Modeling:

The prerequisite relationship for courses is implied and can be modeled using a recursive relationship on the Course entity:

Prerequisite(course_no, prereq_course_no)

This indicates that course_no requires prereq_course_no as a prerequisite.

Both attributes are foreign keys referring to the Course table.

## Design Choices:
Entities were chosen based on the core objects needed to represent a university system: universities, departments, programs, courses, students, and enrollments.

Enrollment was created as a separate entity to capture the M:N relationship between students and courses with an extra attribute (date).

Recursive relationship for prerequisites avoids cluttering the ER diagram while still supporting required functionality.

Faculty and contact information were simplified for diagram clarity but can be extended in implementation.

## RESULT
Successfully designed and explained an ER diagram for a university database with all required entities, relationships, and constraints including support for course prerequisites.

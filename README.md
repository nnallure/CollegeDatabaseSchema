# College Database Schema

This repository contains an SQL schema for a relational database designed to manage information about U.S. states, colleges, degrees offered, and college presidents. The schema uses primary and foreign keys to establish relationships between the entities.

## Database Tables

### 1. **STATE**
Stores information about U.S. states.

- **Columns**:
  - `StateID` (CHAR(2)): Two-character state abbreviation (e.g., `NY`, `CA`). *(Primary Key)*
  - `StateName` (VARCHAR(25)): Full name of the state (e.g., `New York`).
  - `PropNative` (NUMBER(5,4)): Proportion of native residents in the state.

---

### 2. **COLLEGE**
Contains data about colleges located within the states.

- **Columns**:
  - `CollegeID` (CHAR(6)): Unique identifier for each college. *(Primary Key)*
  - `CollegeName` (VARCHAR(80)): Name of the college.
  - `CollegeType` (VARCHAR(7)): Type of college (e.g., `Public`, `Private`).
  - `Students` (NUMBER(4,0)): Number of enrolled students.
  - `StateID` (CHAR(2)): State where the college is located. *(Foreign Key)*

- **Relationships**:
  - Each college belongs to a state (`StateID` references `STATE`).

---

### 3. **DEGREE**
Lists degrees offered by colleges.

- **Columns**:
  - `CollegeID` (CHAR(6)): College offering the degree. *(Foreign Key)*
  - `DegreeName` (VARCHAR(9)): Name of the degree (e.g., `Bachelor`, `Master`). *(Primary Key with `CollegeID`)*

- **Relationships**:
  - Degrees are linked to the colleges that offer them (`CollegeID` references `COLLEGE`).

---

### 4. **PRESIDENT**
Stores information about college presidents.

- **Columns**:
  - `CollegeID` (CHAR(6)): College associated with the president. *(Foreign Key)*
  - `PresidentID` (CHAR(9)): Unique identifier for the president. *(Primary Key)*
  - `Title` (CHAR(3)): Title of the president (e.g., `Dr.`, `Mr.`).
  - `FirstName` (VARCHAR(10)): First name of the president.
  - `LastName` (VARCHAR(15)): Last name of the president.

- **Relationships**:
  - Each president is linked to a college (`CollegeID` references `COLLEGE`).

---

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/CollegeDatabaseSchema.git
2. Import the SQL script into your database management system (e.g., MySQL, PostgreSQL, Oracle).
3. Use the schema to insert data and run queries for your application.

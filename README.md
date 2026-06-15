# Assignment 3: Football Ticket Booking System

## Overview

This project demonstrates the design and implementation of a relational database for a Football Ticket Booking System using PostgreSQL.

The assignment focuses on:

- Database table design
- Primary and Foreign Key relationships
- Data integrity using constraints
- SQL data insertion
- Intermediate SQL queries using joins, subqueries, filtering, sorting, and aggregation

---

## Database Schema

The database contains three main tables:

### 1. Users

Stores information about football fans and ticket managers.

| Column       | Data Type    | Description                    |
| ------------ | ------------ | ------------------------------ |
| user_id      | SERIAL       | Primary Key                    |
| full_name    | VARCHAR(50)  | User's full name               |
| email        | VARCHAR(100) | Unique email address           |
| role         | VARCHAR(50)  | Ticket Manager or Football Fan |
| phone_number | VARCHAR(14)  | Contact number                 |

---

### 2. Matches

Stores football match information.

| Column              | Data Type     | Description                                  |
| ------------------- | ------------- | -------------------------------------------- |
| match_id            | SERIAL        | Primary Key                                  |
| fixture             | VARCHAR(255)  | Match teams                                  |
| tournament_category | VARCHAR(255)  | Tournament name                              |
| base_ticket_price   | DECIMAL(10,2) | Ticket price                                 |
| match_status        | VARCHAR(50)   | Available, Selling Fast, Sold Out, Postponed |

---

### 3. Bookings

Stores ticket booking information.

| Column         | Data Type     | Description                             |
| -------------- | ------------- | --------------------------------------- |
| booking_id     | SERIAL        | Primary Key                             |
| user_id        | INT           | Foreign Key → Users                     |
| match_id       | INT           | Foreign Key → Matches                   |
| seat_number    | VARCHAR(10)   | Seat allocation                         |
| payment_status | VARCHAR(20)   | Pending, Confirmed, Cancelled, Refunded |
| total_cost     | DECIMAL(10,2) | Total booking amount                    |

---

## Relationships

### One-to-Many Relationships

- One User can create multiple Bookings.
- One Match can have multiple Bookings.

### Entity Relationship Diagram (ERD)

Users (1) ------< Bookings >------ (1) Matches

---

## Constraints Used

### Primary Keys

- user_id
- match_id
- booking_id

### Foreign Keys

- bookings.user_id → users.user_id
- bookings.match_id → matches.match_id

### Unique Constraint

- users.email

### Check Constraints

Role values:

- Ticket Manager
- Football Fan

Match Status values:

- Available
- Selling Fast
- Sold Out
- Postponed

Payment Status values:

- Pending
- Confirmed
- Cancelled
- Refunded

Ticket prices and booking costs must be non-negative.

---

## Sample Data

The database contains sample records for:

- 4 Users
- 5 Matches
- 5 Bookings

These records are used to demonstrate query functionality and relationships between tables.

---

## SQL Queries Implemented

### Query 1

Retrieve all available Champions League matches.

### Query 2

Find users whose names start with "Tanvir" or contain "Haque" (case-insensitive).

### Query 3

Display bookings with missing payment status and replace NULL values using COALESCE.

### Query 4

Retrieve booking information along with user names and match fixtures using INNER JOIN.

### Query 5

Display all users and their booking IDs, including users without bookings using LEFT JOIN.

### Query 6

Find bookings where the total cost is greater than the average booking cost using a subquery.

### Query 7

Retrieve the top 2 most expensive matches while skipping the highest-priced match using OFFSET and LIMIT.

---

## Technologies Used

- PostgreSQL
- SQL

---

## Learning Outcomes

Through this assignment, the following database concepts were practiced:

- Relational Database Design
- Primary Keys
- Foreign Keys
- Referential Integrity
- Data Validation using Constraints
- JOIN Operations
- Subqueries
- Aggregate Functions
- NULL Handling
- Sorting and Pagination

---

## Author

Assignment 3 – Football Ticket Booking System

Prepared as part of PostgreSQL Database Practice and SQL Query Development.

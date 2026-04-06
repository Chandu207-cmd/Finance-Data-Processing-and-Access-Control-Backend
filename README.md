# Finance Data Processing & Access Control Backend

## Overview

This project is a backend system for a finance dashboard that manages financial transactions, user roles, and access control. It demonstrates clean backend architecture, API design, business logic implementation, and role-based authorization.

---

## Features

### User & Role Management

* Create and manage users
* Assign roles: **ADMIN, ANALYST, VIEWER**
* Role-based access control

### Transaction Management

* Create, update, delete transactions (ADMIN only)
* View transactions (ALL roles)
* Filter transactions by category (ADMIN, ANALYST)

### Dashboard Summary
Returns structured JSON:

{
  "totalIncome": number,
  "totalExpense": number,
  "balance": number
}

### Access Control

* ADMIN → Full access
* ANALYST → Read + insights
* VIEWER → Read only

### Validation & Error Handling

* Prevent invalid data (negative amount, missing fields)
* Proper error responses

---

## Tech Stack

* Java 21
* Spring Boot
* Spring Data JPA
* H2 Database (in-memory)
* Maven

---

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/your-username/finance-backend.git
```

2. Open in Eclipse / IntelliJ

3. Run:

```
FinanceBackendApplication.java
```

4. Server runs on:

```
http://localhost:8081
```

---

## API Testing (Postman)

### Headers (Required for most APIs)

```
Key: role
Value: ADMIN / ANALYST / VIEWER
```

---

### Create Transaction (ADMIN)

POST `/transactions`

Body:

```json
{
  "amount": 1000,
  "type": "income",
  "category": "salary",
  "date": "2026-04-06",
  "notes": "Monthly salary"
}
```

---

### Get All Transactions

GET `/transactions`

---

### Update Transaction (ADMIN)

PUT `/transactions/{id}`

---

### Delete Transaction (ADMIN)

DELETE `/transactions/{id}`

---

### Filter by Category

GET `/transactions/category/{category}`

---

### Dashboard Summary

GET `/transactions/summary`

---

## Project Structure

```
controller → API layer  
service → business logic  
repository → database access  
model → entities  
dto → data transfer objects  
exception → global error handling  
```

---

## Assumptions

* Role is passed via request header (mock authentication)
* H2 database is used for simplicity
* No authentication system implemented (optional)

---

## Future Improvements

* JWT Authentication
* Pagination
* Filtering by date/type
* API documentation (Swagger)
* Unit testing

---

## Author

Chandu Misanapu

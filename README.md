# Student Management System

A **Student Management System (SMS)** is a full-stack web application that helps educational institutions manage student data, classes, and administrative tasks. This project uses **Node.js, Express, MySQL, Sequelize** for the backend and **React.js** for the frontend.  

The system supports **student registration, login, viewing students by class**, and is ready to be extended with features like **attendance, grades, and messaging**.

---

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
  - [Backend](#backend-setup)
  - [Frontend](#frontend-setup)
- [Usage](#usage)
- [Future Enhancements](#future-enhancements)

---

## Features
- Student registration and login with hashed passwords.
- View all students and their classes.
- Role-based structure ready for teachers/admins.
- Clean RESTful API using Node.js and Express.
- MySQL database with Sequelize ORM.
- React frontend with routing and API integration.

---

## Tech Stack
- **Backend:** Node.js, Express, Sequelize ORM, MySQL, bcrypt, JWT, dotenv
- **Frontend:** React.js, Axios, React Router
- **Database:** MySQL
- **Tools:** nodemon, Postman (for testing API)

---

## Project Structure

### Backend
```

backend/
├── config/
│   └── db.config.js        # Database configuration
├── controllers/
│   └── student.controller.js
├── models/
│   ├── index.js
│   ├── student.model.js
│   ├── class.model.js
│   └── teacher.model.js
├── routes/
│   └── student.routes.js
├── seeders/                # Optional: initial data seeds
├── .env                    # Environment variables
└── server.js               # Main server file

```

### Frontend
```

frontend/
├── src/
│   ├── components/
│   │   ├── Navbar.js
│   │   ├── StudentRegister.js
│   │   ├── StudentLogin.js
│   │   └── StudentList.js
│   ├── pages/
│   │   ├── Home.js
│   ├── services/
│   │   └── studentService.js
│   └── App.js
└── package.json

````

---

## Setup Instructions

### Backend Setup
1. Clone the repository:
```bash
git clone <your-repo-url>
cd student-management-system/backend
````

2. Install dependencies:

```bash
npm install
```

3. Create `.env` file:

```
DB_HOST=localhost
DB_USER=smsuser
DB_PASS=smspass
DB_NAME=sms_db
JWT_SECRET=yourjwtsecret
PORT=5000
```

4. Setup MySQL database:

```sql
CREATE DATABASE sms_db;
USE sms_db;

CREATE TABLE classes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    createdAt DATETIME DEFAULT NOW(),
    updatedAt DATETIME DEFAULT NOW()
);

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    classId INT,
    createdAt DATETIME DEFAULT NOW(),
    updatedAt DATETIME DEFAULT NOW(),
    FOREIGN KEY (classId) REFERENCES classes(id)
    ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE TABLE teachers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    createdAt DATETIME DEFAULT NOW(),
    updatedAt DATETIME DEFAULT NOW()
);
```

5. Seed initial data:

```sql
INSERT INTO classes (name, createdAt, updatedAt) VALUES
('Class 1', NOW(), NOW()),
('Class 2', NOW(), NOW()),
('Class 3', NOW(), NOW());

INSERT INTO students (name, email, password, classId, createdAt, updatedAt) VALUES
('John Doe', 'john@example.com', 'hashedpassword123', 1, NOW(), NOW()),
('Jane Smith', 'jane@example.com', 'hashedpassword123', 2, NOW(), NOW());

INSERT INTO teachers (name, email, password, createdAt, updatedAt) VALUES
('Mr. Smith', 'smith@example.com', 'hashedpassword123', NOW(), NOW());
```

6. Run the backend server:

```bash
nodemon server.js
```

Server runs on **[http://localhost:5000](http://localhost:5000)**

---

### Frontend Setup

1. Navigate to frontend folder:

```bash
cd ../frontend
```

2. Install dependencies:

```bash
npm install
```

3. Start React app:

```bash
npm start
```

Frontend runs on **[http://localhost:3000](http://localhost:3000)**

---

## Usage

* Visit **[http://localhost:3000](http://localhost:3000)** in your browser.
* Use the navigation bar to:

  * **Register Student** → Add new students.
  * **Login** → Student login.
  * **View Students** → See list of all students and their classes.

---

## Future Enhancements

* Attendance tracking per student and class.
* Grades/Marks management per subject.
* Role-based authentication: Admin, Teacher, Student.
* Dashboard with analytics: attendance percentages, average grades.
* Messaging system between teachers and students.
* Export student data as CSV/PDF.

---

**Project Status:** Fully functional **basic SMS**, ready for extensions.

---

**Author:** Md Abdul Qayyum
**Date:** November 2025

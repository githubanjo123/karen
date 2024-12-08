# Student Management System Setup Guide

This guide will help you set up and run the **Student Management System** on a different machine. It involves setting up the backend PHP API and connecting it to a database for storing student information.

## Prerequisites

Before proceeding, ensure you have the following installed:

1. **XAMPP** - Includes Apache, MySQL, and PHP.
2. **NetBeans IDE** - For Java development.
3. **JDK 1.8 or newer** - Java Development Kit.

## Backend Setup (PHP API)

1. **Download the source code** for the PHP API from the GitHub repository.
2. **Move the API folder** to the `htdocs` directory inside your XAMPP installation. The folder should be named `student-api`.
   - Path: `C:\xampp\htdocs\student-api`

3. **Import the database**:
   - Download the `school.sql` file from the repository or your local machine.
   - Open **phpMyAdmin** by running XAMPP and clicking on **Admin** under MySQL.
   - Create a new database named `school`.
   - Import the `school.sql` file into the `school` database:
     - In phpMyAdmin, select the `school` database.
     - Click on the **Import** tab.
     - Choose the `school.sql` file and click **Go**.

4. **Database Credentials**:
   - In the `student.php` file located in the `student-api` folder, make sure the database connection details are correct:
     ```php
     $servername = "localhost";
     $username = "root";
     $password = ""; // Default MySQL password is empty in XAMPP
     $dbname = "school";
     ```

   - The table structure inside the `school.sql` file is as follows:
     ```sql
     CREATE TABLE students (
         id INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(255) NOT NULL,
         course VARCHAR(255) NOT NULL
     );
     ```

## Java Project Setup

1. **Download the source code** for the Java application.
2. **Import the Java project** into **NetBeans**:
   - Open NetBeans and go to **File > Open Project**.
   - Select the folder where you saved the Java project.
   
3. **Setup HTTP Requests**:
   - In your Java application, ensure you are using `HttpURLConnection` to send requests to the PHP API (e.g., POST for adding, PUT for updating, DELETE for deleting).
   
4. **Running the Project**:
   - In NetBeans, select the project and click **Run** to launch the Java application.

## Configuring the PHP API

1. **Start Apache and MySQL** in XAMPP:
   - Open the **XAMPP Control Panel** and start both **Apache** and **MySQL**.
   - Ensure the API can be accessed by visiting `http://localhost/student-api/student.php`.

## Testing the Application

You can now test the application by interacting with the following actions:

- **Add Student**: Use the Java application to add a student to the database.
- **Update Student**: Modify student information using the update feature.
- **Delete Student**: Remove a student from the database using the delete feature.

### Common Issues

1. **404 Error on API Requests**:
   - Ensure that the `student-api` folder is correctly placed in `htdocs` and that XAMPP is running.

2. **Database Connection Issues**:
   - Double-check the database credentials in the `student.php` file and make sure MySQL is running in XAMPP.

---

That's it! You now have the **Student Management System** set up and running on your machine.

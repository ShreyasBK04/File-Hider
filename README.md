# 📂 File Hider App

A **Java + MySQL console-based application** to securely hide and unhide files.
Users sign up and log in with an **OTP verification system** (sent to their email), and then manage files by hiding/unhiding them through a simple command-line menu.

---

## ✨ Features

* 🔑 **User Authentication** with OTP via email (Gmail SMTP).
* 📝 **Signup/Login** with email verification.
* 📂 **Hide Files** – securely stores file paths in the database and marks them as hidden.
* 👀 **Unhide Files** – restores hidden files back.
* 📋 **View Hidden Files** by ID and filename.
* 💾 **MySQL Integration** for persistent storage.

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/ShreyasBK04/File-Hider.git
cd File-Hider
```

### 2. Database Setup

Create a database in MySQL:

```sql
CREATE DATABASE file_hider;
USE file_hider;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE
);

CREATE TABLE files (
    id INT AUTO_INCREMENT PRIMARY KEY,
    file_name VARCHAR(255),
    path VARCHAR(500),
    email VARCHAR(100)
);
```

### 3. Configure Database Connection

Update your JDBC connection details inside `UserDAO` / `DataDAO` with:

```java
String url = "jdbc:mysql://localhost:3306/file_hider";
String user = "root";       // your MySQL username
String password = "your_password";
```

### 4. Configure Email (SMTP)

In `SendOTPService.java`, update:

```java
String from = "your-email@gmail.com";   // your Gmail
String password = "your-app-password";  // Gmail App Password (not your actual password!)
```

⚠️ Use a **Google App Password** instead of your main password for security.
Generate it from Google Account → Security → App Passwords.

### 5. Build and Run

Compile and run using:

```bash
javac -d out src/**/*.java
java -cp out Main
```

---

## 🚀 Usage

1. **Run the app.**
2. Choose:

   * `1 → Login`
   * `2 → Signup`
   * `0 → Exit`
3. If signing up, you’ll get an **OTP via email**. Enter it to register.
4. After login, you can:

   * Show hidden files
   * Hide a new file
   * Unhide a file
   * Exit

---

## 📸 Example Flow

```
Welcome to the app  
Press 1 to login  
Press 2 to signup  
Press 0 to exit  

Enter email: test@gmail.com  
OTP sent to your email...  
Enter OTP: 1234  
Login successful!  

Welcome test@gmail.com  
Press 1 to show hidden files  
Press 2 to hide a new file  
Press 3 to unhide a file  
Press 0 to exit  
```






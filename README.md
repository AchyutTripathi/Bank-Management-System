<div align="center">

# 🏦 Bank Management System

**A desktop banking application built with Java, Swing/AWT, and MySQL — simulating core banking operations through an intuitive GUI.**

[![Java](https://img.shields.io/badge/Java-OOP-orange?style=flat-square&logo=openjdk)](https://openjdk.org/)
[![Swing](https://img.shields.io/badge/Java%20Swing-GUI-blue?style=flat-square&logo=java)](https://docs.oracle.com/javase/tutorial/uiswing/)
[![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?style=flat-square&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![JDBC](https://img.shields.io/badge/JDBC-Connectivity-green?style=flat-square)](https://docs.oracle.com/javase/tutorial/jdbc/)
[![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ%20IDEA-IDE-000000?style=flat-square&logo=intellijidea)](https://www.jetbrains.com/idea/)

</div>

---

## 📖 Overview

The **Bank Management System** is a Java desktop application that simulates essential banking operations through a graphical user interface. Built using Java Swing and AWT for the frontend and MySQL as the backend database, it demonstrates core Object-Oriented Programming principles applied to a real-world banking scenario.

| | |
|---|---|
| **Type** | Desktop GUI Application |
| **Language** | Java |
| **GUI Framework** | Java Swing & AWT |
| **Database** | MySQL via JDBC |
| **IDE** | IntelliJ IDEA |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **Java** | Core application logic and OOP design |
| **Java Swing & AWT** | Graphical user interface (forms, buttons, tables) |
| **JDBC** | Database connectivity between Java and MySQL |
| **MySQL** | Persistent storage for accounts and transactions |
| **IntelliJ IDEA** | Project IDE (`.iml` + `.idea/` configuration included) |

---

## ✨ Features

- 🔐 **User Authentication** — Secure login system for customers and admin
- 👤 **Account Creation** — Register new bank accounts with customer details
- 💰 **Deposit Money** — Add funds to an existing account
- 💸 **Withdraw Money** — Withdraw funds with balance validation
- 🔄 **Fund Transfer** — Transfer money between accounts within the bank
- 📊 **Balance Inquiry** — Check real-time account balance
- 📜 **Transaction History** — View a record of past transactions (mini-statement)
- 🗑️ **Account Management** — Update or delete account information
- 🖥️ **Swing GUI** — Fully graphical interface — no command-line required

---

## ✅ Prerequisites

- **Java JDK** 8 or higher
- **MySQL Server** (local installation or XAMPP/WAMP)
- **MySQL JDBC Driver** (`mysql-connector-java.jar`)
- **IntelliJ IDEA** (recommended) or any Java IDE (Eclipse, NetBeans)

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/AchyutTripathi/Bank-Management-System.git
cd Bank-Management-System
```

### 2. Set up the MySQL database

Open MySQL and create the database and required tables:

```sql
CREATE DATABASE bankdb;
USE bankdb;

CREATE TABLE accounts (
    account_no    VARCHAR(20) PRIMARY KEY,
    holder_name   VARCHAR(100) NOT NULL,
    balance       DECIMAL(15, 2) DEFAULT 0.00,
    account_type  VARCHAR(20),
    pin           VARCHAR(10),
    created_at    TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE transactions (
    id            INT AUTO_INCREMENT PRIMARY KEY,
    account_no    VARCHAR(20),
    type          VARCHAR(20),
    amount        DECIMAL(15, 2),
    txn_date      TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (account_no) REFERENCES accounts(account_no)
);
```

### 3. Configure the database connection

Find the database connection class in the project (typically `Conn.java` or similar) and update your MySQL credentials:

```java
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/bankdb",
    "root",        // your MySQL username
    "yourpassword" // your MySQL password
);
```

### 4. Add the JDBC driver

- Download `mysql-connector-java.jar` from [MySQL Downloads](https://dev.mysql.com/downloads/connector/j/)
- In IntelliJ IDEA: **File → Project Structure → Libraries → + → Java** → select the JAR

### 5. Build and run

**In IntelliJ IDEA:**
1. Open the project: **File → Open** → select the `Bank-Management-System` folder
2. Ensure the JDBC driver is on the classpath (see step 4)
3. Locate the main entry point class (e.g., `Main.java` or `Login.java`)
4. Right-click → **Run**

**From the command line:**
```bash
javac -cp .;mysql-connector-java.jar src/*.java
java -cp .;mysql-connector-java.jar Main
```
> On Linux/macOS, use `:` instead of `;` as the classpath separator.

---

## 📁 Project Structure

```
Bank-Management-System/
├── .idea/                    ← IntelliJ IDEA project settings
├── src/                      ← Java source files
│   ├── Main.java             ← Application entry point
│   ├── Login.java            ← Login screen (GUI)
│   ├── Signup.java           ← New account registration (GUI)
│   ├── Transactions.java     ← Deposit / Withdraw / Transfer (GUI)
│   ├── Balance.java          ← Balance inquiry screen (GUI)
│   ├── MiniStatement.java    ← Transaction history (GUI)
│   ├── Conn.java             ← JDBC database connection helper
│   └── ...                   ← Additional feature classes
├── out/production/           ← Compiled .class files (IntelliJ output)
├── Bank Management System.iml← IntelliJ module file
└── .gitignore
```

> **Note:** The exact class names may vary. Open the `src/` folder in your IDE to explore all files.

---

## 🔄 Application Flow

```
Launch App
    │
    ▼
Login Screen ──── New User? ──── Sign Up / Create Account
    │
    ▼ (authenticated)
Main Dashboard
    │
    ├── Deposit
    ├── Withdraw
    ├── Fund Transfer
    ├── Balance Inquiry
    └── Mini Statement (Transaction History)
```

---

## 🖥️ How to Use

1. **Launch** the application — the Login screen will appear
2. **Sign Up** to create a new account (enter name, account type, initial deposit, PIN)
3. **Log In** using your account number and PIN
4. From the dashboard, choose any operation:
   - **Deposit** — enter an amount to credit to your account
   - **Withdraw** — enter an amount (must not exceed current balance)
   - **Transfer** — enter recipient's account number and amount
   - **Balance** — view your current balance instantly
   - **Mini Statement** — see a list of recent transactions

---

## 🤝 Contributing

```bash
# Fork the repo, then:
git checkout -b feature/your-feature-name
git commit -m "feat: describe your change"
git push origin feature/your-feature-name
# Open a Pull Request
```

---

## 👤 Author

**Achyut Tripathi**
- GitHub: [@AchyutTripathi](https://github.com/AchyutTripathi)

---

<div align="center">
  Built with ☕ Java &nbsp;·&nbsp; 🖥️ Swing &nbsp;·&nbsp; 🐬 MySQL
</div>

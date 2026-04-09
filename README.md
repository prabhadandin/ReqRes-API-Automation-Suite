

# 🎯 API Regression Tests (ReqRes)

## 🔗 Live API Report
https://prabhadandin.github.io/ReqRes-API-Automation-Suite/

---

## 🚀 Project Overview

This repository contains a **REST API Functional Regression Suite** for the [ReqRes.in](https://reqres.in) API.

The goal is to validate:
- User Authentication (Login)
- User Management (CRUD operations)

using **Postman** for test design and **Newman** for CI/CD execution.

---

## 🛠 Tech Stack

- 🧪 Testing Tool: Postman (v11+)
- ⚙️ CLI Runner: Newman
- 📊 Reporting: newman-reporter-htmlextra
- 💻 Language: JavaScript (Chai.js assertions)

---

## ✨ Features

- ✔ CRUD API automation
- ✔ Data-driven testing (JSON / CSV)
- ✔ Postman + Newman execution
- ✔ Dynamic session token management
- ✔ Request chaining (user_id extraction)
- ✔ HTML reporting (Newman HTML Extra)
- ✔ CI/CD integration via GitHub Actions

---

## 🔐 Test Scenarios

### 🔑 Authentication Flow

- Login Success → 200 OK  
  - Stores session_token for further requests  

- Missing Password → 400 Bad Request  
  - Validates error response  

- User Not Found → 400 Bad Request  
  - Validates error message  

---

### 👥 User Management (CRUD)

#### Create User
- Status: 201 Created  
- Uses CSV data (name, job)  
- Stores user_id dynamically  

#### Update User
- Status: 200 OK  
- Updates using stored user_id  
- Validates response body  

#### Delete User
- Status: 204 No Content  
- Cleans environment variables  

---

## ⚙️ Environment Variables

| Variable     | Description              |
|--------------|--------------------------|
| baseUrl      | https://reqres.in       |
| xApiKey      | API Key                 |
| session_key  | Generated after login   |

📌 Import `environment.json` before running tests.

---

## 🚀 CI/CD Pipeline (GitHub Actions)

This project uses **GitHub Actions** to run API tests automatically on push.

---

## 📊 Reports

HTML reports are generated using:

**newman-reporter-htmlextra**

Reports include:
- Passed tests
- Failed assertions
- API response details
- Execution summary

---

## 👥 CRUD Flow Summary

1. Create User (201)
2. Get User (200)
3. Update User (200)
4. Delete User (204)

---

## 🧠 Key Features

- Dynamic Data Chaining (userId extraction)
- Token/session handling via environment variables
- CSV-driven test execution
- Chai.js assertions
- GitHub Actions CI/CD pipeline

---

### ⚡  Notes
-Auth negative scenarios are CSV-driven

-Suite is fully data-driven

-Extendable for more negative test cases

---

## 🛠 Local Execution

```bash
npm install -g newman newman-reporter-htmlextraRun tests:

Run tests:
newman run collection.json \
  -e environment.json \
  -r cli,htmlextra






### 🎯 API Regression Tests (ReqRes)
### 🔗 Live API Report
https://prabhadandin.github.io/ReqRes-API-Automation-Suite/


---

### 🚀 Project Overview

This repository contains a **REST API Functional Regression Suite** for the [ReqRes.in](https://reqres.in) API.

The goal is to validate **User Authentication (Login)** and **User Management (CRUD)** workflows using **Postman** for development and **Newman** for CI/CD integration.

---

### 🛠️ Tech Stack

- 🧪 Testing Tool: Postman (v11+)
- ⚙️ CLI Runner: Newman
- 📊 Reporting: newman-reporter-htmlextra
- 💻 Language: JavaScript (Chai.js assertions)

This project uses CSV data for multiple scenarios including:
- Auth flows
- User CRUD
- Negative testing

---

##✨ Features

✔ CRUD API automation  
✔ Data-driven testing (JSON / CSV)  
✔ Postman + Newman execution  
✔ Dynamic session token management  
✔ Dynamic data chaining between requests  
✔ HTML reporting (Newman HTML Extra)  
✔ CI/CD integration via GitHub Actions  

---

##🔐 Test Scenarios

### Auth Flow

- Login Success → 200 OK  
  - Saves session_token for subsequent requests  

- Login Missing Password → 400 Bad Request  
  - Validates error response  

- User Not Found → 400 Bad Request  
  - Validates error message  

---

### 👥 User Management (CRUD)

#### ✅ Positive Scenarios

- Create User → 201 Created  
  - Creates user with name & job from CSV  
  - Saves user_id for Update/Delete  

- Update User → 200 OK  
  - Updates user using stored user_id  
  - Validates updated data  

- Delete User → 204 No Content  
  - Deletes user and clears environment variables  

---

## ⚡ Notes

1. Auth negative scenarios are CSV-driven  
2. User Management negative tests are not fully included (can be extended)  
3. Entire suite is fully data-driven using CSV files  

---

## ⚙️ Environment Variables

| Variable | Description |
|----------|-------------|
| baseUrl | https://reqres.in |
| xApiKey | API Key |
| session_key | Set after login |

📌 Import `environment.json` before running tests.

---

###🚀 CI/CD Pipeline (GitHub Actions)

This project is integrated with **GitHub Actions CI/CD pipeline**.

###📊 Reports

HTML reports are generated using:

newman-reporter-htmlextra

Reports help visualize:
- Passed tests  
- Failed assertions  
- API response details  👥 CRUD Flow
Create User (201)
Get User (200)
Update User (200)
Delete User (204)
🧠 Key Features
Dynamic Data Chaining (userId extraction)
Token/session handling via environment variables
CSV-driven test execution
Assertion validation using Chai.js
CI/CD pipeline using GitHub Actions
🛠️ Local Execution
npm install -g newman newman-reporter-htmlextra

Run tests:

newman run collection.json \
  -e environment.json \
  -r cli,htmlextra



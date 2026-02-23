 
  🎯 Project Overview
This repository contains a **REST API Functional Regression Suite** for the [ReqRes.in](https://reqres.in) API. 
The goal is to validate User Authentication (Login) and User Management (CRUD) workflows using **Postman** for development and **Newman** for CI/CD integration.

🛠️ Tech Stack
Testing Tool:Postman (v11+)
CLI Runner: Newman
Reporting: Newman-Reporter-HtmlExtra
Language:JavaScript (Chai.js for assertions)

🧪 Test Scenarios
🔐 AuthFlow (Admin & User)
 Login Success (200 OK)
 Login - Missing Password (400 Bad Request)
 Login - User Not Found (400 Bad Request)

⚙️ Environment Variables
The suite requires a `Postman Environment` file with:

| Variable | Description |
| :--- | :--- |
| `baseUrl` | `https://reqres.in` |
| `xApiKey` |  API Key |
| `session_key` | Automatically populated after Login |

Getting Started
1. Clone the repo: `git clone <repo-url>`
2. Install Newman: `npm install -g newman newman-reporter-htmlextra`
3. Run the suite: 
   --bash--
   newman run ReqRes-Collection.json -e ReqRes-qa.json -r cli,htmlextra


👥 UserManagement (CRUD)
Create User (201 Created) & Save userID to environment
Get User Details (200 OK)
Update User (200 OK) & Verify changes
Delete User (204 No Content)

✨ Key Features
Dynamic Data Chaining:Automatically extracts the `userid` from the Create response and passes it to Update/Delete requests.
Session Management:Uses a Bearer token saved in environment variables for user-scoped data.
Assertions:Includes checks resposne status code verification,data validation.
CI/CD Ready:Configured to run via Newman with detailed HTML reporting.


 🚀 ReqRes API Automation Suite
Automated testing suite for ReqRes.in using Postman & Newman.
 📊 Test Execution Results (Newman)
![Newman CLI Results](./screenshots/newman-cli.png)

📈 Detailed HTML Report
![HtmlExtra Report](./screenshots/htmlextra-dashboard.png)

🛠️ Local Execution
To run this suite locally, use:
`newman run ReqRes-Collection.json -e ReqRes-qa.json -r cli,htmlextra`
 
  🎯 Project Overview
This repository contains a **REST API Functional Regression Suite** for the [ReqRes.in](https://reqres.in) API. 
The goal is to validate User Authentication (Login) and User Management (CRUD) workflows using **Postman** for development and **Newman** for CI/CD integration.

🛠️ Tech Stack
Testing Tool:Postman (v11+)
CLI Runner: Newman
Reporting: Newman-Reporter-HtmlExtra
Language:JavaScript (Chai.js for assertions)
 This project uses CSV data for multiple scenarios (Auth flows, User CRUD, negative testing)
     -Created data-driven API tests using CSV for multiple scenarios.
     -Implemented dynamic session token management.
     -Generated HTML reports with Newman.
Test Scenarios
🔐 Auth Flow
-Login Success → 200 OK
-Positive scenario with valid email and password
-Saves session_token for subsequent requests
-Login - Missing Password → 400 Bad Request
-Negative scenario when password is not provided
-Validates error message (Missing password or user not found)
-Login - User Not Found → 400 Bad Request
-Negative scenario with invalid email
-Validates error message (user not found)
👥 User Management (CRUD)
✅ Positive Scenarios
-Create User → 201 Created
   Creates user with name and job from CSV
   Saves user_id to environment for Update/Delete
-Update User → 200 OK
   Updates user job using new_user_id from Create step
   Validates updated data against CSV
-Delete User → 204 No Content
   Deletes user using new_user_id from Create step
   Clears environment variable after deletion

⚡ Notes
The current suite does not include explicit negative tests for User Management (invalid IDs, missing fields, unauthorized access).
Auth Flow negative tests are already implemented via CSV-driven scenarios.
All workflows are data-driven, using CSV rows for multiple users and scenarios.

⚙️ Environment Variables
The suite requires a `Postman Environment` file with:

| Variable | Description |
| :--- | :--- |
| `baseUrl` | `https://reqres.in` |
| `xApiKey` |  API Key |
| `session_key` | Automatically populated after Login |

Note: Import reqres-qa.postman_environment.json and add your own api_key from the ReqRes dashboard to run the tests.

Getting Started
1. Clone the repo: `git clone <repo-url>`
2. Install Newman: `npm install -g newman newman-reporter-htmlextra`
3. Run the suite: 
   --bash--
   newman run reqres-csv.postman_collection.json -e reqres-qa.postman_environment.json -r cli,htmlextra

👥 UserManagement (CRUD)
Create User (201 Created) & Save userID to environment
Get User Details (200 OK)
Update User (200 OK) & Verify changes
Delete User (204 No Content)

✨ Key Features
Dynamic Data Chaining:Automatically extracts the `userid` from the Create response and passes it to Update/Delete requests.
Session Management:Uses a Bearer token saved in environment variables for user-scoped data.
Assertions:Includes checks response status code verification,data validation.
CI/CD Ready:Configured to run via Newman with detailed HTML reporting.

🛠️ Local Execution
To run this suite locally, use:
`newman run csvsuite.json -e environment.json -r cli,htmlextra`




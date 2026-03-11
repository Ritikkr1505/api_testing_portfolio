# QA API Testing Portfolio Project

This project demonstrates API testing using Postman and Newman automation.
The APIs tested in this project are taken from the public API:

https://reqres.in

---

## Tools Used

* Postman
* Newman
* Newman HTML Extra Reporter
* Git
* GitHub

---

## APIs Tested

| Method | Endpoint          | Description                  |
| ------ | ----------------- | ---------------------------- |
| GET    | /api/users?page=2 | Get list of users            |
| GET    | /api/users/2      | Get single user              |
| GET    | /api/users/999    | Get single user (Not Found)  |
| POST   | /api/users        | Create user                  |
| POST   | /api/login        | Login user                   |
| POST   | /api/login        | Login (Missing Password)     |

---

## Test Coverage

The following validations are performed:

* Status code validation (200, 201, 400, 404)
* Response body validation
* Data existence validation
* API response time validation (< 2000ms)
* Schema validation
* Field-level validation
* Email format validation
* Negative test scenarios

Example Postman assertions used:

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response time is less than 2000ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(2000);
});

pm.test("Validate response schema", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('data');
});
```

---

## Project Structure

```
qa-api-testing-portfolio
│
├── Test-Scenarios
│   └── api_test_scenarios.xlsx
│
├── Test-Cases
│   └── api_test_cases.xlsx
│
├── Postman-Collection
│   ├── reqres_collection.json
│   └── reqres_environment.json
│
├── Test-Reports
│   └── report.html
│
├── Bug-Reports
│
└── README.md
```

---

## Running Tests Using Newman

Install Newman globally:

```
npm install -g newman
```

Install HTML Extra Reporter:

```
npm install -g newman-reporter-htmlextra
```

Run the Postman collection:

```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json
```

Generate automation report:

```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json -r cli,htmlextra --reporter-htmlextra-export Test-Reports/report.html
```

---

## Test Report

After running Newman, the automation report will be generated in:

```
Test-Reports/report.html
```

Open this file in the browser to view detailed execution results including request details, assertions, and response times.

---

## Author

QA Automation Portfolio Project
Created to demonstrate API testing and automation skills using Postman and Newman.
# api_testing_portfolio

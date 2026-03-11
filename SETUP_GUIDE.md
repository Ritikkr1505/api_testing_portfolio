# Setup and Usage Guide

## Prerequisites

- Node.js (v14 or higher)
- npm (Node Package Manager)
- Postman (optional, for manual testing)

---

## Installation Steps

### 1. Install Newman

```bash
npm install -g newman
```

### 2. Install Newman HTML Extra Reporter

```bash
npm install -g newman-reporter-htmlextra
```

### 3. Verify Installation

```bash
newman --version
```

---

## Running Tests

### Option 1: Run with Environment File (Recommended)

```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json
```

### Option 2: Generate HTML Report

```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json -r cli,htmlextra --reporter-htmlextra-export Test-Reports/report.html
```

### Option 3: Run with Iterations

```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json -n 3
```

### Option 4: Run with Delay Between Requests

```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json --delay-request 1000
```

---

## Environment Variables

The collection uses the following environment variables:

| Variable   | Description              | Default Value        |
| ---------- | ------------------------ | -------------------- |
| baseUrl    | API base URL             | https://reqres.in    |
| x-api-key  | API authentication key   | (configured in env)  |

---

## Test Scenarios Covered

### Positive Test Cases
1. ✅ Get list of users with pagination
2. ✅ Get single user by valid ID
3. ✅ Create new user with valid data
4. ✅ Login with valid credentials

### Negative Test Cases
1. ✅ Get user with invalid ID (404)
2. ✅ Login without password (400)

---

## Viewing Test Reports

After running tests with HTML reporter:

1. Navigate to `Test-Reports/` folder
2. Open `report.html` in your browser
3. Review:
   - Total requests
   - Passed/Failed tests
   - Response times
   - Request/Response details

---

## Importing Collection to Postman

1. Open Postman
2. Click **Import** button
3. Select `Postman-Collection/reqres_collection.json`
4. Import environment: `Postman-Collection/reqres_environment.json`
5. Select the environment from dropdown
6. Run collection manually or use Collection Runner

---

## CI/CD Integration

### GitHub Actions Example

```yaml
name: API Tests

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install Newman
        run: |
          npm install -g newman
          npm install -g newman-reporter-htmlextra
      - name: Run Tests
        run: newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json -r cli,htmlextra
      - name: Upload Report
        uses: actions/upload-artifact@v2
        with:
          name: test-report
          path: newman/
```

---

## Troubleshooting

### Issue: Newman not found
**Solution:** Ensure Node.js and npm are installed, then reinstall Newman globally

### Issue: Collection fails to run
**Solution:** Verify the JSON file is valid and environment variables are set correctly

### Issue: Tests timeout
**Solution:** Check internet connection and API availability at https://reqres.in

---

## Best Practices

1. ✅ Use environment variables for configuration
2. ✅ Include both positive and negative test cases
3. ✅ Validate response time in all tests
4. ✅ Check response schema and data types
5. ✅ Generate reports for every test run
6. ✅ Keep test data separate from test logic
7. ✅ Document all test scenarios

---

## Contact

For questions or issues, please refer to the project documentation or create an issue in the repository.

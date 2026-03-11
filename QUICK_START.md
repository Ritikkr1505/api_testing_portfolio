# Quick Start Guide

## Run Tests Immediately

### 1. Basic Test Run
```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json
```

### 2. Generate HTML Report
```bash
newman run Postman-Collection/reqres_collection.json -e Postman-Collection/reqres_environment.json -r cli,htmlextra --reporter-htmlextra-export Test-Reports/report.html
```

---

## What's New? 🎉

### ✅ 6 API Tests (was 4)
- Get Users List
- Get Single User ⭐ (now has tests!)
- Get Single User - Not Found ⭐ (new negative test)
- Create User
- Login
- Login - Missing Password ⭐ (new negative test)

### ✅ 25 Test Assertions (was 4)
- Status code validation
- Response time validation (< 2000ms)
- Schema validation
- Field validation
- Email format validation

### ✅ Environment Variables
- No more hardcoded URLs
- Secure API key management
- Easy configuration updates

### ✅ New Documentation
- SETUP_GUIDE.md - Detailed instructions
- IMPROVEMENTS.md - Complete changelog
- bug_report_template.md - Bug reporting template
- .gitignore - Protect sensitive files

---

## View Results

After running tests, open:
```
Test-Reports/report.html
```

---

## Import to Postman

1. Open Postman
2. Import → `Postman-Collection/reqres_collection.json`
3. Import → `Postman-Collection/reqres_environment.json`
4. Select "ReqRes Environment" from dropdown
5. Run collection

---

## Key Files

| File                          | Purpose                      |
| ----------------------------- | ---------------------------- |
| reqres_collection.json        | Updated test collection      |
| reqres_environment.json       | Environment variables        |
| README.md                     | Project documentation        |
| SETUP_GUIDE.md                | Detailed setup instructions  |
| IMPROVEMENTS.md               | Complete changelog           |

---

**Ready to test!** 🚀

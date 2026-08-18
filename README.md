# 🚀 Postman API Automation Testing & CI/CD Health Check

> A practical API automation testing project built with **Postman + Newman + GitHub Actions**, demonstrating API validation, automated regression testing, scheduled health checks, test reporting, and failure notification.

[![Automated Postman API Tests](https://github.com/tonychi455448/postman-api-tests/actions/workflows/postman-test.yml/badge.svg)](https://github.com/tonychi455448/postman-api-tests/actions)
![Node.js](https://img.shields.io/badge/Node.js-%3E%3D20-brightgreen)
![Postman](https://img.shields.io/badge/Postman-API%20Testing-orange)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-blue)

---

## 📌 Project Overview

This project demonstrates a complete **API automated testing workflow** using Postman and Newman.

The test suite can be executed locally or automatically through GitHub Actions. It supports **Push / Pull Request / Scheduled Cron / Manual execution**, generates HTML test reports, stores execution artifacts, and automatically creates a GitHub Issue when API assertions fail.

The project is designed to demonstrate practical **Software QA / SDET capabilities**, including:

- API test case design
- Automated regression testing
- Test assertions and response validation
- CLI-based test execution
- CI/CD integration
- Scheduled service health checks
- Automated test reporting
- Failure notification and defect tracking

---

## ⭐ Key Features

### 🤖 1. Automated API Regression Testing

Automatically executes the Postman Collection through Newman.

- API request and response validation
- HTTP status code assertions
- Response time validation
- JSON structure and data type validation
- Dynamic variable passing between APIs
- Regression testing through CI automation

### 🔄 2. GitHub Actions CI/CD Integration

API tests are automatically triggered by:

- `push`
- `pull_request`
- `workflow_dispatch`
- Scheduled `cron`

This allows API tests to become part of the software delivery workflow instead of relying only on manual verification.

### ⏰ 3. Scheduled API Health Check

A scheduled GitHub Actions workflow executes the API test suite every day at:

**00:00 Taiwan Time (UTC+8)**  
**16:00 UTC**

This provides a simple automated mechanism for continuously checking API availability and behavior.

### 📊 4. Automated HTML Test Reports

After each test execution, `newman-reporter-htmlextra` generates a visual HTML report containing test execution details and statistics.

The report is uploaded as a GitHub Actions Artifact for later review.

### 🚨 5. Automated Failure Notification

When API assertions fail:

1. Newman returns a failure exit code.
2. GitHub Actions marks the workflow as failed.
3. A JavaScript-based GitHub API process automatically creates a GitHub Issue.
4. The issue can be used as a starting point for debugging and defect tracking.

### 🔐 6. Environment & Secret Management

Test environment configuration and sensitive credentials are separated from the test logic.

The workflow supports GitHub Secrets for protecting API Keys, Tokens, and other sensitive information.

---

## 🧪 Testing Strategy

The API test cases focus on several common QA validation dimensions.

| Validation Area | Test Objective |
|---|---|
| **HTTP Status Code** | Verify expected status codes such as `200 OK` and `201 Created` |
| **Response Time** | Verify API response time remains below the defined threshold, e.g. `< 2000 ms` |
| **JSON Validation** | Validate response structure, required fields, and data types |
| **Dynamic Variables** | Pass data between API requests using Postman variables |
| **Authentication** | Obtain and reuse tokens across API requests |
| **Regression Testing** | Re-execute the collection automatically after code changes |
| **Health Check** | Periodically verify API availability and expected behavior |

### Example Test Flow

```text
Authentication
      ↓
Obtain Token
      ↓
Pass Token to Next Request
      ↓
Send API Request
      ↓
Validate Status Code
      ↓
Validate Response Time
      ↓
Validate JSON Data
      ↓
Generate Test Report
```

---

## 🛠️ Tech Stack

| Category | Technology | Purpose |
|---|---|---|
| **API Testing** | Postman | API request design and test case development |
| **Test Runner** | Newman | CLI-based automated execution |
| **Test Reporting** | newman-reporter-htmlextra | HTML test report generation |
| **CI/CD** | GitHub Actions | Automated test execution and scheduling |
| **Scripting** | JavaScript / Node.js 20+ | Test logic and GitHub API automation |
| **Version Control** | Git / GitHub | Source control and workflow integration |

---

## 📁 Repository Structure

```text
postman-api-tests/
├── .github/
│   └── workflows/
│       └── postman-test.yml       # GitHub Actions workflow
├── collection.json                # Postman API test collection
├── environment.json               # Postman environment variables
└── README.md                      # Project documentation
```

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/tonychi455448/postman-api-tests.git
cd postman-api-tests
```

### 2. Install Newman

```bash
npm install -g newman newman-reporter-htmlextra
```

### 3. Run API Tests

Create the report directory:

```bash
mkdir -p newman
```

Execute the Postman Collection:

```bash
newman run collection.json   -e environment.json   -r cli,htmlextra   --reporter-htmlextra-export newman/report.html
```

After execution, open:

```text
newman/report.html
```

to review the detailed test results.

---

## 🔄 CI/CD Workflow

The GitHub Actions workflow is defined in:

```text
.github/workflows/postman-test.yml
```

### Workflow

```text
┌──────────────────────────────┐
│ Push / Pull Request / Cron   │
│ Manual workflow_dispatch     │
└──────────────┬───────────────┘
               ↓
      Ubuntu GitHub Runner
               ↓
      Install Node.js & Newman
               ↓
      Execute Postman Tests
               ↓
        ┌──────┴──────┐
        ↓             ↓
      PASS           FAIL
        ↓             ↓
 Generate Report   Create GitHub Issue
        ↓             ↓
 Upload Artifact   Defect Tracking
```

### Execution & Reporting

- **Push:** Test the API after changes are pushed.
- **Pull Request:** Run regression tests before merging.
- **Cron:** Execute scheduled API health checks.
- **Manual:** Trigger the workflow directly from GitHub Actions.
- **Artifacts:** Download `postman-html-report.zip` from the corresponding workflow run.
- **Failure handling:** Failed API assertions return exit code `1` and trigger the automated Issue creation process.

---

## 💡 QA Engineering Practices Demonstrated

This project focuses on the complete automated testing lifecycle rather than only writing API requests.

```text
Test Planning
      ↓
Test Case Design
      ↓
API Test Automation
      ↓
Automated Execution
      ↓
Result Validation
      ↓
Test Reporting
      ↓
Failure Detection
      ↓
Defect Tracking
```

This demonstrates practical experience in:

- **API Automation Testing**
- **Regression Testing**
- **CI/CD Test Integration**
- **Test Result Reporting**
- **Automated Failure Handling**
- **Defect Tracking**
- **Linux / CLI Test Execution**
- **JavaScript Automation**
- **Git / GitHub Workflow**

---

## 🎯 Why This Project Matters

The goal of this project is to demonstrate how API testing can evolve from **manual verification** into a repeatable and maintainable automation workflow.

Instead of simply executing API requests manually:

```text
Manual API Testing
       ↓
Postman Test Cases
       ↓
Newman Automation
       ↓
GitHub Actions
       ↓
Scheduled Regression / Health Check
       ↓
Automated Reporting
       ↓
Failure → GitHub Issue
```

This approach helps reduce repetitive manual testing and provides earlier feedback when API behavior changes.

---

## 👤 Author

**Tony Chi**

Software / Automation QA Engineer

**Focus Areas**

`API Testing` · `Test Automation` · `CI/CD` · `Python` · `Playwright` · `Postman` · `Linux` · `HIL Testing`

GitHub: [@tonychi455448](https://github.com/tonychi455448)

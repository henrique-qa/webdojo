# 🥋 WebDojo — QA Automation Lab

> A full-stack practice environment designed to build and showcase end-to-end test automation skills using **Cypress**.

---

## 📌 About

WebDojo is a containerized web application used as a personal QA Automation study lab. The project covers real-world scenarios including **UI testing**, **API validation**, **chatbot interaction testing**, and **database-backed workflows**.

This repository represents a **hands-on automation portfolio**, demonstrating senior-level proficiency in test architecture, custom commands, reusable fixtures, and maintainable test design patterns.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Test Framework** | Cypress 13+ |
| **Frontend (AUT)** | React + Vite (pre-built) |
| **Backend / DB** | Node.js API + PostgreSQL 13 |
| **Infrastructure** | Docker & Docker Compose |
| **DB Admin** | pgAdmin 4 |
| **Runtime** | Node.js 22+ |

---

## 📁 Project Structure

```
webdojo-main/
├── api/                  # Backend API (Node.js)
├── web/                  # Frontend application (pre-built dist)
│   └── dist/             # Static production build
├── cypress/              # Cypress test suite
│   ├── e2e/              # End-to-end test specs
│   ├── support/          # Custom commands & global setup
│   └── fixtures/         # Test data files
├── docker-compose.yaml   # Infrastructure orchestration
├── cypress.config.js     # Cypress configuration
└── .gitignore
```

---

## ⚙️ Environment Setup

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Node.js 22+](https://nodejs.org/)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)

### 1. Start Infrastructure

```bash
docker compose up -d
```

This will start:
- **PostgreSQL** on port `5432`
- **pgAdmin** on port `15432` → http://localhost:15432

### 2. Start the Web Application

```bash
cd web
npm install
npm run dev
```

App will be available at: **http://localhost:3000**

### 3. Configure Cypress

Create a `cypress.env.json` file at the project root (never commit this file):

```json
{
  "BASE_URL": "http://localhost:3000",
  "DB_USER": "dba",
  "DB_PASSWORD": "dba",
  "DB_NAME": "UserDB"
}
```

---

## 🧪 Running Tests

```bash
# Open Cypress UI
npx cypress open

# Run all tests headlessly
npx cypress run

# Run a specific spec
npx cypress run --spec "cypress/e2e/login.cy.js"
```

---

## 🔒 Security Notes

- Database credentials in `docker-compose.yaml` are **for local development only**
- Never commit `cypress.env.json` or any file containing real credentials
- The `.gitignore` is configured to exclude all sensitive files

---

## 🏗️ Tested Scenarios

- [x] User authentication (login / logout)
- [x] User registration & form validation
- [x] Chatbot interaction & tracking flow
- [x] API contract validation
- [x] Negative test scenarios

---

*Personal QA Automation study project — built to demonstrate test engineering skills.*

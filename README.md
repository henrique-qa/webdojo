# 🥋 WebDojo — QA Automation Lab

> A full-stack practice environment designed to build and showcase end-to-end test automation skills using **Cypress**.

---

## 📌 About

WebDojo is a containerized web application used as a personal QA Automation study lab. The project covers real-world scenarios including **UI testing**, **API interception**, **drag-and-drop**, **iFrame interaction**, **hover events**, and **form validation**.

This repository represents a **hands-on automation portfolio**, demonstrating proficiency in test architecture, custom commands, reusable fixtures, and maintainable test design patterns.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Test Framework** | Cypress 14+ |
| **Real Events** | cypress-real-events |
| **Frontend (AUT)** | React + Vite (pre-built) |
| **Backend / DB** | Node.js API + PostgreSQL 13 |
| **Infrastructure** | Docker & Docker Compose |
| **DB Admin** | pgAdmin 4 |
| **Runtime** | Node.js 22+ |

---

## 📁 Project Structure

```
webdojo/
├── cypress/                  # Cypress test suite (root-level)
│   ├── e2e/                  # End-to-end test specs
│   │   ├── login.cy.js
│   │   ├── alerts.cy.js
│   │   ├── cep.cy.js
│   │   ├── consultancy.cy.js
│   │   ├── github.cy.js
│   │   ├── hover.cy.js
│   │   ├── iframe.cy.js
│   │   ├── kanban.cy.js
│   │   ├── links.cy.js
│   │   └── studio.cy.js
│   ├── fixtures/             # Test data (JSON, PDF)
│   └── support/
│       ├── commands.js       # Custom Cypress commands
│       ├── e2e.js            # Global setup
│       ├── utils.js          # Helper functions
│       └── actions/          # Page-action abstractions
├── web/                      # Frontend application
│   ├── dist/                 # Pre-built static assets
│   └── package.json          # Frontend serve script
├── api/                      # Backend API (Node.js)
├── cypress.config.js         # Cypress configuration
├── package.json              # Root: test scripts
├── docker-compose.yaml       # Infrastructure orchestration
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

### 3. Install Cypress dependencies

From the **project root**:

```bash
npm install
```

### 4. Configure environment (optional)

Create a `cypress.env.json` at the project root (never commit this file):

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

Run from the **project root**:

```bash
# Open Cypress interactive UI
npm run test:ui

# Run all tests headlessly (desktop viewport)
npm test

# Run login spec only — desktop
npm run test:login

# Run login spec only — mobile viewport
npm run test:login:mobile
```

---

## 🔒 Security Notes

- Database credentials in `docker-compose.yaml` are **for local development only**
- Never commit `cypress.env.json` or any file containing real credentials
- The `.gitignore` is configured to exclude all sensitive files and Cypress artifacts (videos, screenshots)

---

## 🏗️ Tested Scenarios

| Spec | Scenario |
|------|----------|
| `login.cy.js` | Auth flow, cookie & localStorage token validation |
| `alerts.cy.js` | JS alert, confirm dialog, prompt stub |
| `cep.cy.js` | API interception (ViaCEP) |
| `consultancy.cy.js` | Complex form — PF/PJ, file upload, required fields |
| `github.cy.js` | Table CRUD, link attributes |
| `hover.cy.js` | Real mouse hover via `cypress-real-events` |
| `iframe.cy.js` | iFrame element interaction |
| `kanban.cy.js` | Drag & drop between columns |
| `links.cy.js` | `target="_blank"` validation & navigation |
| `studio.cy.js` | Cypress Studio generated test example |

---

*Personal QA Automation study project — built to demonstrate test engineering skills.*

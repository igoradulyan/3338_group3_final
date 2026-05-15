# Product Expiration Tracking App

A mobile application for tracking household or personal product expiration dates. Users manually enter product information, store items in a secure account, and receive reminders before products expire.

> **Current project scope:** Manual product entry only. Barcode scanning and AI scanning are intentionally not included in the current version.

---

## Project Overview

The Product Expiration Tracking App helps users reduce waste, save money, and avoid using expired products. The application allows users to create an account, add products manually, enter expiration dates, organize items by category or storage location, and view products that are expired or close to expiration.

The system is designed as a mobile-first application with a React Native frontend, a Node.js backend API, and a PostgreSQL database. Docker Compose is used to run the backend, database, and optional mobile development container.

---

## Main Features

- User registration and login
- Secure authentication using JSON Web Tokens
- Manual product entry
- Product name, category, quantity, location, and expiration date fields
- Product list view
- Product detail view
- Edit and delete product records
- Expiration status tracking
- Search, filter, and sort products
- Reminder settings for upcoming expiration dates
- Backend REST API for mobile app communication
- PostgreSQL database storage
- Docker-based development environment

---

## Technology Stack

### Frontend

- React Native
- Expo
- JavaScript or TypeScript
- React Navigation
- Axios or Fetch API
- AsyncStorage or SecureStore for token storage

### Backend

- Node.js
- Express.js
- PostgreSQL
- Prisma, Sequelize, or Knex for database access
- bcrypt for password hashing
- jsonwebtoken for authentication
- dotenv for environment variables
- cors for frontend-backend communication

### DevOps / Development Tools

- Docker
- Docker Compose
- Git and GitHub
- npm
- TestRail for test case management
- Jira for project planning and backlog tracking
- LaTeX for formal documentation

---

## High-Level Architecture

```text
User
 |
 | uses mobile app
 v
React Native Mobile App
 |
 | HTTPS / REST API requests
 v
Node.js Express Backend
 |
 | database queries
 v
PostgreSQL Database
```

The user interacts with the React Native mobile application. The mobile app sends API requests to the Node.js backend. The backend validates requests, applies business logic, and stores or retrieves data from PostgreSQL. Only authenticated users can access their own product data.

---

## Project Folder Structure

Recommended structure:

```text
product-expiration-tracker/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── models/
│   │   ├── middleware/
│   │   ├── services/
│   │   └── app.js
│   ├── package.json
│   ├── Dockerfile
│   └── .env
│
├── mobile/
│   ├── src/
│   │   ├── screens/
│   │   ├── components/
│   │   ├── navigation/
│   │   ├── services/
│   │   └── utils/
│   ├── package.json
│   ├── Dockerfile
│   └── app.json
│
├── docs/
│   ├── Product_Expiration_Tracking_SRS.tex
│   ├── Product_Expiration_Tracking_SDD.tex
│   ├── Product_Expiration_Tracking_Design_Spec.tex
│   ├── Product_Expiration_Tracking_Snapshot_Objectives.tex
│   └── Product_Expiration_Tracking_Workflow.tex
│
├── docker-compose.yml
└── README.md
```

---

## Core Pages and Screens

### Authentication Screens

- Welcome screen
- Register screen
- Login screen
- Logout option

### Product Screens

- Dashboard screen
- Product list screen
- Add product screen
- Product detail screen
- Edit product screen
- Expired products screen
- Soon-to-expire products screen

### Settings Screens

- Reminder settings
- Account settings
- App information screen

---

## Example Product Fields

Each product record may include:

- Product name
- Category
- Quantity
- Storage location
- Expiration date
- Notes
- Created date
- Updated date
- User ID owner reference

Example:

```json
{
  "name": "Milk",
  "category": "Dairy",
  "quantity": 1,
  "location": "Refrigerator",
  "expirationDate": "2026-05-30",
  "notes": "Bought from local grocery store"
}
```

---

## Backend API Endpoints

Possible REST API endpoints:

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Create a new user account |
| POST | `/api/auth/login` | Log in and receive token |
| GET | `/api/products` | Get all products for logged-in user |
| POST | `/api/products` | Create a new product manually |
| GET | `/api/products/:id` | Get one product by ID |
| PUT | `/api/products/:id` | Update product information |
| DELETE | `/api/products/:id` | Delete a product |
| GET | `/api/products/expiring-soon` | Get products close to expiration |
| GET | `/api/products/expired` | Get expired products |
| GET | `/api/settings/reminders` | Get reminder settings |
| PUT | `/api/settings/reminders` | Update reminder settings |

---

## Docker Setup

This project includes a `docker-compose.yml` file for running the application services.

### Services

- `postgres`: PostgreSQL database
- `backend`: Node.js / Express backend API
- `mobile`: Optional React Native / Expo development container

### Start the Project

From the project root, run:

```bash
docker compose up --build
```

### Stop the Project

```bash
docker compose down
```

### Stop and Remove Volumes

```bash
docker compose down -v
```

Use this only when you want to remove the database data.

---

## Environment Variables

Example backend `.env` file:

```env
NODE_ENV=development
PORT=3000
DATABASE_URL=postgresql://expiration_user:expiration_password@postgres:5432/expiration_tracker
JWT_SECRET=change_this_secret_before_production
JWT_EXPIRES_IN=1d
CORS_ORIGIN=http://localhost:8081
```

For production, secrets should be stored securely and not committed to GitHub.

---

## Testing

Testing should include manual testing, backend API testing, and regression testing.

Recommended test areas:

- User registration
- User login
- Invalid login handling
- Add product manually
- Edit product
- Delete product
- View product list
- Filter by expiration status
- Search by product name
- Verify expired product calculation
- Verify soon-to-expire product calculation
- Confirm one user cannot access another user’s products
- Confirm barcode scanning and AI scanning are not present in the current version

A TestRail-ready CSV file is included in the documentation package.

---

## Jira Planning

The project can be managed in Jira using the recommended project key:

```text
PET
```

Suggested Jira project name:

```text
Product Expiration Tracking App
```

The backlog is organized into epics, user stories, technical tasks, QA tasks, and snapshot-based development milestones.

---

## Snapshot Plan

### Snapshot 1: Project Foundation

- Create project structure
- Set up React Native mobile app
- Set up Node.js backend
- Set up PostgreSQL database
- Configure Docker Compose
- Create initial documentation

### Snapshot 2: Authentication and Product Creation

- Implement registration
- Implement login
- Add JWT authentication
- Create manual add product screen
- Create product database table
- Connect frontend to backend API

### Snapshot 3: Product Management and Expiration Tracking

- Display product list
- Add product detail screen
- Edit product records
- Delete product records
- Add expiration status logic
- Add expired and soon-to-expire views

### Snapshot 4: Final Integration and Testing

- Add reminder settings
- Improve UI/UX
- Complete API validation
- Complete TestRail test cases
- Finalize Jira backlog
- Finalize LaTeX documentation
- Prepare final project submission

---

## Documentation Included

The project documentation package includes:

- Software Requirements Specification
- Software Design Document
- Design Specification
- Snapshot Objectives
- Workflow Diagram
- Docker Compose YAML file
- TestRail test cases
- Jira backlog CSV
- Jira setup guide
- README file

---

## Security Notes

- Passwords must be hashed before storage.
- JWT secrets must not be exposed publicly.
- API routes that access product data must require authentication.
- Users should only access their own product records.
- Database credentials should be stored in environment variables.
- Production deployments should use HTTPS.

---

## Current Limitations

- Manual entry only
- No barcode scanning
- No AI scanning
- No image recognition
- No shared family account support in the first version
- No web dashboard in the first version

These features may be considered for future versions after the core application is complete.

---

## Future Enhancements

Possible future improvements:

- Push notifications
- Family/shared household accounts
- Product categories customization
- Export product list
- Cloud deployment
- Analytics dashboard
- Grocery list integration
- Barcode scanning after manual-entry version is complete
- AI-assisted product entry after manual-entry version is complete

---

## Author

Prepared for a software engineering project using:

- React Native frontend
- Node.js backend
- PostgreSQL database
- Docker development environment


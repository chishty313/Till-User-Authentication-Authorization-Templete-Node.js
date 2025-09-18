# Till-User-Authentication-Authorization-Template-Node.js

A boilerplate backend project for learning and reusing **Node.js + Express + MongoDB** authentication & authorization flows.  
This repository will evolve step-by-step into a complete, documented template.

---

## 1️⃣ Product Requirements Document (PRD)

### Template Code Till User Authentication & Authorization Backend

#### 1. Product Overview
**Product Name:** TBD  
**Version:** 1.0.0  
**Product Type:** Backend API for …

#### 2. Target Users
TBD

#### 3. Core Features

##### 3.1 User Authentication & Authorization
- **User Registration:** Account creation with email verification  
- **User Login:** Secure authentication with JWT tokens  
- **Password Management:** Change password, forgot/reset password functionality  
- **Email Verification:** Account verification via email tokens  
- **Token Management:** Access token refresh mechanism  
- **Role-Based Access Control:** Three-tier permission system (Admin, Project Admin, Member)

##### 3.2 System Health
- **Health Check:** API endpoint for system status monitoring

#### 4. Technical Specifications

##### 4.1 API Endpoints Structure

**Authentication Routes** (`/api/v1/auth/`)
- `POST /register` – User registration  
- `POST /login` – User authentication  
- `POST /logout` – User logout (secured)  
- `GET /current-user` – Get current user info (secured)  
- `POST /change-password` – Change user password (secured)  
- `POST /refresh-token` – Refresh access token  
- `GET /verify-email/:verificationToken` – Email verification  
- `POST /forgot-password` – Request password reset  
- `POST /reset-password/:resetToken` – Reset forgotten password  
- `POST /resend-email-verification` – Resend verification email (secured)

**Health Check** (`/api/v1/healthcheck/`)
- `GET /` – System health status

##### 4.3 Data Models

**User Roles:**
- `admin` – Full system access  
- `project_admin` – Project-level administrative access  
- `member` – Basic project member access

**Task Status:**
- `todo` – Task not started  
- `in_progress` – Task currently being worked on  
- `done` – Task completed

#### 5. Security Features
- JWT-based authentication with refresh tokens  
- Role-based authorization middleware  
- Input validation on all endpoints  
- Email verification for account security  
- Secure password reset functionality  
- File upload security with Multer middleware  
- CORS configuration for cross-origin requests

---

## 2️⃣ Current Progress

- Initialized Git repository and connected to GitHub  
- Ran `npm init` to create `package.json`  
- Added basic project metadata (name, description, author, license, keywords)  
- Created entry point `index.js` with a simple `console.log("Hello World")`

---

## 3️⃣ Project Setup

> Ensure [Node.js](https://nodejs.org/) (v18+) and [Git](https://git-scm.com/) are installed.

```bash
# Clone the repo
git clone https://github.com/chishty313/Till-User-Authentication-Authorization-Templete-Node.js.git

# Go to project folder
cd Till-User-Authentication-Authorization-Templete-Node.js

# Install dependencies (none yet, but run after packages are added)
npm install

# Start the app
npm run dev
```

Running `npm run dev` prints:

```
Hello World
```

---

## 4️⃣ Code Formatting with Prettier

To maintain a consistent coding style across the project, [Prettier](https://prettier.io/) is used as the code formatter.

### Installation

```bash
npm install --save-dev --save-exact prettier
```

### Configuration

Two files were created in the project root:

#### `.prettierrc`

```json
{
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": false,
  "trailingComma": "all",
  "bracketSpacing": true,
  "arrowParens": "always"
}
```

#### `.prettierignore`

```text
# Ignore artifacts:
build
coverage
node_modules
env
```

> This ensures build outputs, coverage reports, dependencies, and environment files are not formatted.

### Usage

Format all files in the repository:

```bash
npx prettier . --write
```

### `.gitignore`

Also add common exclusions to `.gitignore`:

```text
node_modules
.env
```

> Prevents large dependency folders and sensitive environment variables from being committed.

---

## 5️⃣ Developer Utilities

### 5.1 Nodemon

[Nodemon](https://www.npmjs.com/package/nodemon) automatically restarts the application when files change.

#### Installation

```bash
npm install --save-dev nodemon
```

#### Scripts in `package.json`

```json
"scripts": {
  "dev": "nodemon index.js",
  "start": "node index.js"
}
```

#### Usage

Start the app in development mode:

```bash
npm run dev
```

---

### 5.2 Environment Variables with dotenv

[dotenv](https://www.npmjs.com/package/dotenv) is used to load environment variables from a `.env` file into `process.env`.

#### Installation

```bash
npm install dotenv
```

#### Usage in `index.js`

```javascript
import dotenv from "dotenv";

dotenv.config({
  path: "./.env",
});

console.log("Hello World");
console.log("Hello World");
```

> Place your environment-specific settings inside a `.env` file (e.g., database credentials, API keys).  
> Ensure `.env` is listed in `.gitignore` to keep it private.

---

## 6️⃣ Project Folder Structure

The project is organized for scalability and clarity:
```bash
Till-User-Authentication-Authorization-Template-Node.js/
├── node_modules/
├── public/
│ └── images/
│ └── .gitkeep
├── src/
│ ├── controllers/
│ ├── db/
│ ├── middlewares/
│ ├── models/
│ ├── routes/
│ ├── utils/
│ ├── validators/
│ └── index.js
├── .env
├── .gitignore
├── .prettierignore
├── .prettierrc
├── package.json
└── README.md
```

> `public/images/.gitkeep` ensures Git tracks the otherwise-empty `images` folder.

---

## 6️⃣ Express Setup

[Express](https://www.npmjs.com/package/express) is used as the web framework for building APIs and handling routes.

### Installation

```bash
npm install express --save
```

### Basic Server Setup

`src/index.js`:
```javascript
import dotenv from "dotenv";
import express from "express";

dotenv.config({
  path: "./.env",
});

const app = express();
const port = process.env.PORT || 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening on port http://localhost:${port}`);
});
```
### Environment Variables

`.env`:
```ini
PORT=8000
```

> The server will use the port specified in .env, or default to 3000 if not set.

### Usage
```bash
npm run dev
```

Visit `http://localhost:8000` to see the output:
```javascript
Hello World!
```

---

## 8️⃣ Add Middlewares (Body Parsing, Static, CORS)

To prepare for handling requests and cross-origin access, add middleware in `src/app.js`.

### Updated `src/app.js`

```javascript
import express from "express";
import cors from "cors";

const app = express();

// Basic Configurations
app.use(express.json({ limit: "16kb" }));
app.use(express.urlencoded({ extended: true, limit: "16kb" }));
app.use(express.static("public"));

app.use(
  cors({
    origin: process.env.CORS_ORIGIN?.split(",") || "http://localhost:5173",
    credentials: true,
    methods: ["GET", "POST", "PUT", "DELETE", "OPTIONS"],
    allowedHeaders: ["Content-Type", "Authorization"],
  }),
);

app.get("/", (req, res) => {
  res.send("Hello World!");
});

export default app;
```

### `.env` file:
```bash
PORT=8000
CORS_ORIGIN=*
# (e.g., https://example.com, https://another.com)
```

> CORS_ORIGIN can be a comma-separated list of allowed domains, or * for development.

---

## 9️⃣ Standard API & Error Response Classes

To make our responses consistent across the app, we’ll create two utility classes:  
`ApiResponse` for successful responses and `ApiError` for errors.

### `src/utils/ApiResponse.js`

```javascript
class ApiResponse {
  constructor(statusCode, data, message = "Success") {
    this.statusCode = statusCode;
    this.data = data;
    this.message = message;
    this.success = statusCode < 400;
  }
}

export { ApiResponse };
```

`src/utils/ApiError.js`

```javascript
class ApiError extends Error {
  constructor(
    statusCode,
    message = "Something went wrong",
    error = [],
    stack = "",
  ) {
    super(message);
    this.statusCode = statusCode;
    this.data = null;
    this.message = message;
    this.success = false;
    this.error = error;

    if (stack) {
      this.stack = stack;
    } else {
      Error.captureStackTrace(this, this.constructor);
    }
  }
}

export { ApiError };
```

> These classes will be used in controllers, services, and middleware to send uniform responses.

---

## 6️⃣ Roadmap

- [ ] Project folder structure  
- [ ] Express server + Health Check endpoint  
- [ ] User model with Mongoose  
- [ ] Authentication routes (register/login/logout)  
- [ ] JWT & refresh tokens  
- [ ] Email verification & password reset  
- [ ] Role-based authorization middleware  
- [ ] Finalize README with API reference

---
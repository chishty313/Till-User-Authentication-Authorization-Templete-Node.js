# Till-User-Authentication-Authorization-Template-Node.js

A boilerplate backend project for learning and reusing **Node.js + Express + MongoDB** authentication & authorization flows.
This repository will evolve step-by-step into a complete, documented template.

---

## 1️⃣ Current Progress

- Initialized Git repository and connected to GitHub
- Ran `npm init` to create `package.json`
- Added basic project metadata (name, description, author, license, keywords)
- Created entry point `index.js` with a simple `console.log("Hello World")`

---

## 2️⃣ Project Setup

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

## 3️⃣ Roadmap

- [ ] Project folder structure
- [ ] Express server + Health Check endpoint
- [ ] User model with Mongoose
- [ ] Authentication routes (register/login/logout)
- [ ] JWT & refresh tokens
- [ ] Email verification & password reset
- [ ] Role-based authorization middleware
- [ ] Finalize README with API reference

---
4️⃣ Code Formatting with Prettier

To maintain a consistent coding style across the project, Prettier
 is used as the code formatter.

Installation
# Install Prettier as a dev dependency (exact version)
npm install --save-dev --save-exact prettier

Configuration

Two files were created in the project root:

.prettierrc
{
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": false,
  "trailingComma": "all",
  "bracketSpacing": true,
  "arrowParens": "always"
}

.prettierignore
# Ignore artifacts:
build
coverage
node_modules
env


This ensures build outputs, coverage reports, dependencies, and environment files are not formatted.

Usage

Format all files in the repository:

npx prettier . --write

.gitignore

Also add common exclusions to .gitignore:

node_modules
.env


Prevents large dependency folders and sensitive environment variables from being committed.

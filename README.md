# AI-Codebase-Archaeologist

> An AI-powered developer tool that allows users to upload a codebase and interact with it using natural language to understand its structure, files, functionality, and code.

---

# 1. 🎯 What Problem Does It Solve?

When developers join an existing project, they often face questions like:

- Where is authentication handled?
- What does this component do?
- How does the frontend communicate with the backend?
- Which file connects to MongoDB?
- How does the login flow work?
- Can you explain this project to me?

Normally, developers have to spend hours reading and understanding the codebase.

The **AI Codebase Explainer** allows developers to upload their project and ask questions about it using natural language.

The goal is to make understanding an unfamiliar codebase much faster.

---

# 2. 👤 User Flow

The complete Version 1 flow:

```text
                    User
                     │
                     ▼
              Create Account
                     │
                     ▼
               Dashboard
                     │
                     ▼
             Upload ZIP File
                     │
                     ▼
             Extract Project
                     │
                     ▼
          Analyze Project Files
                     │
                     ▼
       ┌─────────────┴─────────────┐
       ▼                           ▼
 Project Overview              File Explorer
       │                           │
       ▼                           ▼
 AI Summary                  Select a file
       │                           │
       └──────────────┬────────────┘
                      ▼
                 Ask AI Questions
                      │
                      ▼
                   Gemini
                      │
                      ▼
                  AI Answer


```



3. 🛠️ Tech Stack
Frontend
React + Vite
Used for:

Dashboard

Login/Register

File upload

Project explorer

Chat interface

AI responses

Additional Frontend Libraries
React Router → Routing

Axios → API requests

Tailwind CSS → Styling

Lucide React → Icons

Backend
Node.js + Express
Responsible for:

Authentication

File uploads

ZIP extraction

Project processing

Gemini API communication

Database operations

Useful Packages
express
mongoose
jsonwebtoken
bcrypt
multer
unzipper
dotenv
cors
Database
MongoDB
Store:

Users
Projects
Files
Chat History
Initially, the complete codebase does not need to be stored directly in MongoDB.

Project metadata and extracted files can be stored separately depending on the deployment strategy.

AI
Google Gemini API
Gemini can be used for:

Project summary

File explanation

Code explanation

Question answering

Technology identification

Documentation generation

Initially, we will not use RAG or embeddings.

Authentication
JWT + bcrypt
Authentication flow:

Register
   ↓
Hash Password
   ↓
MongoDB

Login
   ↓
Verify Password
   ↓
Generate JWT
   ↓
Frontend Stores Token
Protected routes require a valid JWT.

File Processing
Use:

Multer → Receive ZIP files

Unzipper / JSZip → Extract ZIP files

Then inspect files such as:

package.json
src/
routes/
controllers/
models/
components/
README.md


4. 🖥️ Main Pages
The application can initially contain around 6 main pages.

① Landing Page
A simple marketing/home page.

Example:

AI Codebase Explainer

Understand any codebase in minutes.

[Upload Your Project]
Features:

What the application does

How it works

Technology stack

Login/Register buttons

② Login/Register
Standard authentication interface.

Email
Password

[Login]

Don't have an account?
Register
③ Dashboard
After logging in:

Hello, Developer 👋

Your Projects

┌─────────────────────┐
│ E-commerce App      │
│ React + Node + Mongo│
│ Updated 2 hours ago │
└─────────────────────┘

┌─────────────────────┐
│ Chat Application    │
│ MERN                │
│ Updated yesterday   │
└─────────────────────┘

       [+ New Project]
The dashboard displays the user's projects.

5. 📦 Project Upload
User clicks:

New Project
Then:

Upload your project

┌────────────────────────────┐
│                            │
│       📁 Drop ZIP here     │
│                            │
│      or browse files       │
│                            │
└────────────────────────────┘

          [Analyze Project]
After upload:

Uploading...
██████████████░░░░

Extracting files...
Analyzing project...

✓ Project uploaded
✓ Files detected
✓ Technologies identified
✓ Project summary generated
6. 🧠 Project Overview
This is one of the most important screens.

Example:

E-Commerce Application

Technology
────────────────
React
Node.js
Express
MongoDB
JWT

Project Structure
────────────────
Frontend
Backend
Database

AI Overview
────────────────

"This project is a full-stack e-commerce
application. The frontend is built using
React while the backend uses Express..."

Important Files
────────────────

📄 App.jsx
📄 server.js
📄 User.js
📄 authController.js
📄 productController.js
Gemini generates the project overview.

7. 📂 File Explorer
Create a simple file browser.

Example:

Project
│
├── frontend
│   ├── components
│   ├── pages
│   ├── App.jsx
│   └── main.jsx
│
├── backend
│   ├── controllers
│   ├── models
│   ├── routes
│   └── server.js
│
├── package.json
└── README.md
When the user clicks:

authController.js
Show:

┌─────────────────────────────────────┐
│ authController.js                   │
├─────────────────────────────────────┤
│                                     │
│ const loginUser = async (...) => {  │
│     ...                             │
│ }                                   │
│                                     │
└─────────────────────────────────────┘

        [✨ Explain This File]



8. 🤖 AI Code Explanation
When the user clicks:

Explain This File
The backend sends the file contents to Gemini.

Gemini responds with something like:

### What this file does

This file handles user authentication.

### Main responsibilities

• Validates user credentials
• Checks the user in MongoDB
• Generates a JWT token
• Returns the authenticated user

### Important functions

loginUser()
Handles the login request...

generateToken()
Creates the JWT...
This is one of the primary AI features.

9. 💬 AI Codebase Chat
Create a ChatGPT-like interface.

Example:

┌────────────────────────────────────────┐
│          AI Codebase Assistant         │
├────────────────────────────────────────┤
│                                        │
│ You:                                   │
│ How does authentication work?          │
│                                        │
│ AI:                                    │
│ Authentication is handled through      │
│ JWT tokens. The main flow starts in    │
│ authController.js...                   │
│                                        │
│ You:                                   │
│ Where is the JWT generated?            │
│                                        │
│ AI:                                    │
│ The token is generated in...           │
│                                        │
├────────────────────────────────────────┤
│ Ask about your code...           [➤]  │
└────────────────────────────────────────┘
Important
Version 1 will NOT use RAG.

Initially, provide Gemini with:

Project summary

Relevant selected files

User's question

Later, RAG can be introduced to automatically find the relevant files.




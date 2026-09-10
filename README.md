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

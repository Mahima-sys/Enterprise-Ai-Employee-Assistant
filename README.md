# Enterprise-Ai-Employee-Assistant
An enterprise-grade AI Employee Assistant built with React, FastAPI, TypeScript, and Google Gemini.
  ## 🚀 Features

### 🔐 Authentication
- User registration and login
- Password hashing
- JWT-based authentication
- Protected API endpoints
- Secure user authentication flow

### 💬 AI Employee Chat
- Conversational AI assistant
- Natural language interaction
- Employee-focused questions and answers
- Gemini-powered responses
- Context-aware conversations
- Chat history storage

### 📚 RAG - Retrieval Augmented Generation

The assistant can answer questions based on uploaded company documents.

Supported knowledge sources include:

- Employee Handbook
- HR SOP
- Leave Policy
- Other organizational documents

The project uses:

- Document processing
- Text extraction
- Embeddings
- FAISS vector database
- Retrieval-based context
- Gemini for final response generation

### 📄 Document Management

Employees/admins can upload organizational documents.

Uploaded documents can be processed and added to the vector store so that the AI assistant can use them when answering questions.

### 📊 Dashboard

The application includes an employee dashboard for displaying useful information and application statistics.

### 📈 Analytics

Analytics APIs are included for tracking application usage and employee assistant activity.

### 🧠 AI Services

The backend contains separate AI and RAG service layers to keep AI-related functionality modular and maintainable.

---

# 🏗️ Project Architecture

```text
enterprise-ai-employee-assistant/
│
├── backend/
│   │
│   ├── app/
│   │   ├── agents/
│   │   │
│   │   ├── api/
│   │   │   └── routes/
│   │   │       ├── analytics.py
│   │   │       ├── auth.py
│   │   │       ├── chat.py
│   │   │       ├── dashboard.py
│   │   │       └── document.py
│   │   │
│   │   ├── auth/
│   │   │   ├── auth.py
│   │   │   ├── dependencies.py
│   │   │   ├── hashing.py
│   │   │   └── jwt_handler.py
│   │   │
│   │   ├── config/
│   │   │
│   │   ├── core/
│   │   │
│   │   ├── database/
│   │   │   └── database.py
│   │   │
│   │   ├── models/
│   │   │   ├── user.py
│   │   │   ├── chat.py
│   │   │   └── document.py
│   │   │
│   │   ├── schemas/
│   │   │   ├── user.py
│   │   │   └── chat.py
│   │   │
│   │   ├── security/
│   │   │   └── auth.py
│   │   │
│   │   ├── services/
│   │   │   ├── ai_service.py
│   │   │   └── rag_service.py
│   │   │
│   │   ├── uploads/
│   │   │
│   │   ├── utils/
│   │   │
│   │   ├── vectorstore/
│   │   │   ├── index.faiss
│   │   │   └── index.pkl
│   │   │
│   │   ├── main.py
│   │   └── memory.py
│   │
│   ├── uploads/
│   ├── enterprise_ai.db
│   ├── .env
│   ├── requirements.txt
│   └── venv/
│
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
│
├── docker/
│
├── docs/
│
└── README.md
```
---

## 🛠️ Technology Stack
Frontend
React
TypeScript
Vite
Axios
HTML
CSS
JavaScript
Backend
Python
FastAPI
Uvicorn
Pydantic
SQLAlchemy
SQLite
Artificial Intelligence
Google Gemini
Generative AI
Retrieval-Augmented Generation (RAG)
Embeddings
FAISS
Authentication
JWT
Password hashing
Secure authentication dependencies
Database
SQLite
SQLAlchemy ORM

---

## 📂 Backend Structure

The backend follows a modular architecture.

app/main.py

Main FastAPI application.

It initializes the FastAPI server and registers the API routes.

The backend is started using:

uvicorn app.main:app --reload

The API will be available at:

http://127.0.0.1:8000

Swagger API documentation:

http://127.0.0.1:8000/docs

---
## 🔐 Authentication

Authentication is implemented using JWT tokens.

The authentication system contains:

app/auth/
├── auth.py
├── dependencies.py
├── hashing.py
└── jwt_handler.py

Authentication flow:

User
 │
 ▼
Login Page
 │
 ▼
React Frontend
 │
 ▼
POST /login
 │
 ▼
FastAPI
 │
 ▼
Database User Verification
 │
 ▼
Password Verification
 │
 ▼
JWT Token
 │
 ▼
Authenticated User
💬 Chat Architecture

The employee assistant follows this flow:

Employee
   │
   ▼
React Chat Interface
   │
   ▼
Axios Request
   │
   ▼
FastAPI /chat
   │
   ▼
AI Service
   │
   ├──────────────┐
   │              │
   ▼              ▼
Gemini         RAG Service
                  │
                  ▼
              FAISS Vector Store
                  │
                  ▼
            Relevant Documents
   │              │
   └───────┬──────┘
           ▼
       AI Response
           │
           ▼
     React Frontend

     ---

## 📚 RAG System

The project uses Retrieval-Augmented Generation to allow the AI assistant to answer questions using internal company documents.

Example documents:

Employee-Handbook.pdf
HR SOP.pdf
Leave-Policy.pdf

The documents are processed and stored in the vector store.

Current vector store files:

app/vectorstore/
├── index.faiss
└── index.pkl

When an employee asks a question:

Question
   ↓
Embedding
   ↓
FAISS similarity search
   ↓
Relevant document chunks
   ↓
Gemini
   ↓
Final answer

This reduces the need for the AI model to rely only on general knowledge.

📄 Document Upload

Documents can be uploaded through the document API.

The uploaded documents are stored in the project's upload directories.

Example:

app/uploads/
├── Employee-Handbook.pdf
├── HR SOP.pdf
└── Leave-Policy.pdf

The document service processes these files and makes their information available to the RAG pipeline.

---

## 🗄️ Database

The project uses SQLite for development.

Database:

enterprise_ai.db

The database contains application data such as:

Users
Chat information
Documents
Application-related records

SQLAlchemy is used for database interaction.

---

## 🖥️ Frontend

The frontend is built using:

React
TypeScript
Vite
Axios

The frontend communicates with the FastAPI backend through HTTP APIs.

Example:

Frontend
http://localhost:5173
       │
       │ Axios
       ▼
Backend
http://127.0.0.1:8000
⚙️ Installation
1. Clone the repository
git clone <your-github-repository-url>
cd enterprise-ai-employee-assistant
🐍 Backend Setup

Go to the backend directory:

cd backend

Create a virtual environment:

python -m venv venv

Activate it on Windows:

.\venv\Scripts\activate

Install dependencies:

pip install -r requirements.txt

---

 ## 🔑 Environment Variables

Create a .env file inside the backend directory.

Example:

GEMINI_API_KEY=your_gemini_api_key

SECRET_KEY=your_secret_key

ALGORITHM=HS256

ACCESS_TOKEN_EXPIRE_MINUTES=30

Do not commit .env to GitHub.

Add it to .gitignore:

.env
venv/
__pycache__/
*.pyc

---

## ▶️ Run Backend

From the backend directory:

.\venv\Scripts\activate

Then:

uvicorn app.main:app --reload

Backend:

http://127.0.0.1:8000

Swagger documentation:

http://127.0.0.1:8000/docs

---

## ⚛️ Frontend Setup

Open another terminal.

Go to the frontend directory:

cd frontend

Install dependencies:

npm install

Start the development server:

npm run dev

Frontend will normally run at:

http://localhost:5173
🔗 Frontend + Backend Connection

The frontend communicates with the backend using Axios.

Example:

import axios from "axios";

const response = await axios.post(
  "http://127.0.0.1:8000/login",
  {
    email,
    password
  }
);

The architecture is:

React
  ↓
Axios
  ↓
FastAPI
  ↓
Services
  ↓
Database / Gemini / RAG

---

## 🌐 CORS

The FastAPI backend allows requests from the React development server.

Typical development frontend origins:

http://localhost:5173
http://localhost:5174

CORS is required because the frontend and backend run on different ports during development.

🔌 API Endpoints

The project contains API routes for:

Authentication
POST /login

Authentication-related functionality handles:

Login
User verification
Password validation
JWT authentication
Chat
POST /chat

Used by the employee assistant to process user questions.

Documents

Document-related APIs handle:

Uploading documents
Processing documents
Managing knowledge sources
Dashboard

Dashboard APIs provide employee/application information.

Analytics

Analytics APIs provide application usage information.

### 🧪 Testing

Run the backend:

uvicorn app.main:app --reload

Open:

http://127.0.0.1:8000/docs

Use Swagger UI to test the APIs.

For frontend testing:

npm run dev

Then open:

http://localhost:5173

## 🐛 Troubleshooting
Uvicorn cannot import main

If you see:

Error loading ASGI app.
Could not import module "main".

Make sure you are inside:

backend

and use:

uvicorn app.main:app --reload

not:

uvicorn main:app --reload
PowerShell blocks npm

If PowerShell shows:

npm.ps1 cannot be loaded

you can use:

npm.cmd run dev

Or update the current user's PowerShell execution policy:

Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

Then:

npm run dev
401 Unauthorized during login

If the browser reaches the backend but shows:

401 Unauthorized

this generally means the login request reached FastAPI successfully but the supplied credentials were rejected.

Check:

Email/username
Password
Existing user record
Password hash
Database connection

A 401 is different from a frontend-backend connection failure.

---

## 🔒 Security

Important security practices:

Never expose Gemini API keys
Never commit .env
Use hashed passwords
Use JWT authentication
Validate API requests
Protect private endpoints
Keep database credentials secure

--- 

## 📈 Future Enhancements

Planned improvements include:

- Advanced AI agent capabilities
- n8n workflow automation
- Automated employee workflows
- Email integration
- Calendar integration
- Leave request automation
- HR ticket creation
- Improved RAG pipeline
- Better document management
- Role-based access control
- Admin dashboard
- Advanced analytics
- Persistent conversational memory
- Enterprise integrations
- Docker deployment
- Cloud deployment

---
## 🎯 Project Objective

The goal of this project is to build an intelligent enterprise employee assistant capable of combining:

Generative AI
+
RAG
+
Enterprise Documents
+
Authentication
+
Database
+
Automation

to provide employees with a centralized AI-powered workplace assistant.

---

## 👩‍💻 Author

Mahi Pothuraju

B.Tech – Computer Science and Engineering

Vignana Bharathi Institute of Technology (VBIT)

---

## ⭐ Project Highlights
- Full-stack AI application
- React + TypeScript frontend
- FastAPI backend
- Gemini-powered AI
- RAG implementation
- FAISS vector search
- JWT authentication
- Password hashing
- SQLite database
- Document processing
- Employee-focused AI assistant
- Modular backend architecture

  ## Sample  Images

  "C:\Users\pothu\OneDrive\Pictures\Screenshots\Screenshot 2026-07-03 204923.png"

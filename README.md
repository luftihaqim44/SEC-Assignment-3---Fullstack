# TaskFlow Studio - Final Fullstack Project

TaskFlow Studio is a fullstack task management application with authentication, task CRUD, and advanced task query features. It includes a React frontend, Express backend API, and SQLite database.

## Features Implemented

- User register/login with JWT authentication
- Protected frontend routes based on login state
- Task CRUD operations (create/read/update/delete)
- Search, filtering, sorting, and pagination for tasks
- Loading states and error handling in all key views
- Responsive UI with 4 meaningful views:
  - Dashboard
  - Task list board
  - New task form
  - Task details/edit

## Tech Stack

- Frontend: React + Vite + React Router
- Backend: Node.js + Express
- Validation: Zod
- Auth: JWT + bcryptjs
- Database: SQLite (better-sqlite3)

## Project Structure

- `backend/` -> Express API and SQLite data
- `frontend/` -> React single page application

## Database Schema (Summary)

`users`
- `id` INTEGER PRIMARY KEY
- `name` TEXT NOT NULL
- `email` TEXT UNIQUE NOT NULL
- `password_hash` TEXT NOT NULL
- `role` TEXT NOT NULL DEFAULT 'user'
- `created_at` TEXT

`tasks`
- `id` INTEGER PRIMARY KEY
- `user_id` INTEGER NOT NULL (FK -> users.id)
- `title` TEXT NOT NULL
- `description` TEXT
- `status` TEXT CHECK ('todo', 'in_progress', 'done')
- `priority` TEXT CHECK ('low', 'medium', 'high')
- `due_date` TEXT
- `created_at` TEXT
- `updated_at` TEXT

## Local Setup

### 1. Backend

```bash
cd backend
cp .env.example .env
npm install
npm run seed
npm run dev
```

Backend runs on `http://localhost:4000` by default.

Seeded demo login:
- Email: `demo@taskflow.dev`
- Password: `demo12345`

### 2. Frontend

```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```

Frontend runs on `http://localhost:5173` by default.

## API Endpoint Summary

Base URL: `http://localhost:4000/api`

Auth
- `POST /auth/register`
- `POST /auth/login`

Tasks (Bearer token required)
- `GET /tasks` (supports query params: `search`, `status`, `priority`, `sortBy`, `sortOrder`, `page`, `pageSize`)
- `POST /tasks`
- `GET /tasks/:id`
- `PUT /tasks/:id`
- `DELETE /tasks/:id`

Health
- `GET /health`

## Deployment Notes

- Frontend can be deployed on Vercel/Netlify.
- Backend can be deployed on Render/Railway.
- If deploying separately, set frontend `VITE_API_URL` to deployed backend URL.

## Assignment Mapping

- Core fullstack functionality: complete frontend + backend + persistent DB integration
- Advanced features: authentication + search/filter/sort/pagination
- Frontend UX: forms, data display, loading/error states, multi-page flow
- Backend quality: clean route/controller/service split with validation and error handling

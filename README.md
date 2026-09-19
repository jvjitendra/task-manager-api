# TaskFlow — Full-Stack Task Manager

A portfolio-ready full-stack task management application.

## Architecture

Frontend:
- HTML
- CSS
- Vanilla JavaScript
- Deployed separately on Vercel

Backend:
- Flask REST API
- SQLAlchemy + SQLite
- JWT authentication
- Password hashing
- Docker
- Railway deployment

## Features

- User registration and login
- JWT authentication
- Protected task routes
- Create, read, update and delete tasks
- Task statuses: Pending, In Progress, Completed
- Search and sorting
- Dashboard statistics
- Responsive UI
- Frontend consumes the live REST API

## Backend API

- POST `/api/register`
- POST `/api/login`
- POST `/api/tasks`
- GET `/api/tasks`
- GET `/api/tasks/<id>`
- PUT `/api/tasks/<id>`
- DELETE `/api/tasks/<id>`

## Run backend

```powershell
cd backend
pip install -r requirements.txt
python app.py
```

Backend: `http://localhost:5000`

## Run frontend locally

Because the frontend is plain HTML/CSS/JS, you can open `frontend/index.html` directly for basic testing. For a cleaner local setup, use VS Code Live Server.

Before testing, check `frontend/config.js` and make sure `API_BASE_URL` points to your Railway backend.

## Deployment

1. Push backend to GitHub and deploy to Railway.
2. Generate the Railway public domain.
3. Update `frontend/config.js` with that domain.
4. Deploy the `frontend` folder to Vercel.
5. Test Register → Login → Create Task → Update Status → Edit → Delete.

## Important

The backend uses SQLite. On Railway, SQLite storage can be ephemeral depending on the deployment/storage setup. For a production system, PostgreSQL would be a better database choice.

## Interview explanation

“I built a full-stack Task Management application. The backend is a Flask REST API with JWT authentication and SQLAlchemy. I Dockerized and deployed the backend on Railway, then built a responsive vanilla JavaScript frontend that consumes the REST endpoints for authentication and task CRUD operations.”

## Project structure

```text
task-manager-fullstack/
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
├── frontend/
│   ├── index.html
│   ├── style.css
│   ├── app.js
│   └── config.js
└── README.md
```

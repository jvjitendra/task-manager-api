# Task Manager REST API (JWT Auth + Docker)

A production-style backend REST API with JWT-based authentication and full CRUD for task management — built with Flask, SQLAlchemy, and Docker.

## Features
- User registration & login with hashed passwords (Werkzeug)
- JWT token-based authentication (24hr expiry)
- Protected routes — only logged-in users can access their own tasks
- Full CRUD: Create, Read, Update, Delete tasks
- Dockerized for easy deployment
- SQLite (swap to MySQL/Postgres by changing `SQLALCHEMY_DATABASE_URI`)

## Tech Stack
`Python` `Flask` `Flask-SQLAlchemy` `PyJWT` `SQLite` `Docker`

## Project Structure
```
task-manager-api/
├── app.py              # Main application (models, routes, auth)
├── requirements.txt    # Dependencies
├── Dockerfile           # Container config
└── README.md
```

## Setup — Local

```bash
pip install -r requirements.txt
python app.py
```
Server runs at `http://localhost:5000`

## Setup — Docker

```bash
docker build -t task-manager-api .
docker run -p 5000:5000 task-manager-api
```

## API Endpoints

| Method | Endpoint | Auth Required | Description |
|--------|----------|----------------|-------------|
| POST | `/api/register` | No | Register new user |
| POST | `/api/login` | No | Login, returns JWT token |
| POST | `/api/tasks` | Yes | Create a task |
| GET | `/api/tasks` | Yes | Get all tasks of logged-in user |
| GET | `/api/tasks/<id>` | Yes | Get a single task |
| PUT | `/api/tasks/<id>` | Yes | Update a task |
| DELETE | `/api/tasks/<id>` | Yes | Delete a task |

Protected routes need header: `Authorization: Bearer <token>`

### Example — Register
```bash
curl -X POST http://localhost:5000/api/register \
  -H "Content-Type: application/json" \
  -d '{"username":"jitendra","password":"test123"}'
```

### Example — Login
```bash
curl -X POST http://localhost:5000/api/login \
  -H "Content-Type: application/json" \
  -d '{"username":"jitendra","password":"test123"}'
```

### Example — Create Task
```bash
curl -X POST http://localhost:5000/api/tasks \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <TOKEN>" \
  -d '{"title":"Learn Docker","description":"Complete docker basics"}'
```

## Deployment
Deployed live on Render/Railway — free tier. Push this repo to GitHub, connect to Render, set start command `python app.py`.

## Author
Jitendra Kumar Verma — [GitHub](https://github.com/jvjitendra)

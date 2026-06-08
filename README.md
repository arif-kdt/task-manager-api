# Task Manager API

A RESTful API for task management built with Django and Django REST Framework. Features JWT authentication, task CRUD operations, filtering, and search.

## 🌐 Live API

Base URL: `https://task-manager-api-production-ba15.up.railway.app/api/`

| Endpoint | Method | Auth Required |
|----------|--------|---------------|
| `/auth/register/` | POST | No |
| `/auth/login/` | POST | No |
| `/auth/refresh/` | POST | No |
| `/auth/profile/` | GET | Yes |
| `/tasks/` | GET, POST | Yes |
| `/tasks/<id>/` | GET, PATCH, DELETE | Yes |
| `/tasks/stats/` | GET | Yes |

## 🛠 Tech Stack

- **Backend:** Python, Django 6, Django REST Framework
- **Authentication:** JWT (SimpleJWT)
- **Database:** SQLite (development) / PostgreSQL (production)
- **Tools:** Postman, Git

## 🚀 Features

- User registration and JWT authentication
- Create, read, update, and delete tasks
- Filter tasks by status and priority
- Search tasks by title and description
- Each user sees only their own tasks

## ⚙️ Local Setup

```bash
# Clone the repository
git clone https://github.com/arif-kdt/task-manager-api.git
cd task-manager-api

# Create virtual environment
python -m venv venv
venv\Scripts\activate  # Windows
source venv/bin/activate  # Mac/Linux

# Install dependencies
pip install -r requirements.txt

# Create .env file
cp .env.example .env

# Run migrations
python manage.py migrate

# Start server
python manage.py runserver
```

## 📌 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register/` | Register a new user |
| POST | `/api/auth/login/` | Login and get JWT tokens |
| POST | `/api/auth/refresh/` | Refresh access token |
| GET | `/api/auth/profile/` | Get current user profile |

### Tasks
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tasks/` | List all tasks |
| POST | `/api/tasks/` | Create a new task |
| GET | `/api/tasks/<id>/` | Get a single task |
| PATCH | `/api/tasks/<id>/` | Update a task |
| DELETE | `/api/tasks/<id>/` | Delete a task |

## 🔍 Filtering & Search

```
GET /api/tasks/?status=pending
GET /api/tasks/?priority=high
GET /api/tasks/?search=meeting
GET /api/tasks/?ordering=-created_at
```

## 📦 Task Object

```json
{
    "id": 1,
    "user": {
        "id": 1,
        "username": "arif",
        "email": "arif@example.com"
    },
    "title": "Build Task Manager API",
    "description": "Complete the Django REST API project",
    "priority": "high",
    "status": "in_progress",
    "due_date": "2026-06-14",
    "created_at": "2026-06-07T18:35:08Z",
    "updated_at": "2026-06-07T18:35:08Z"
}
```

## 🔐 Authentication

All task endpoints require a JWT token in the header:
```
Authorization: Bearer <your_access_token>
```

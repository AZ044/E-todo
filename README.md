# ETodo Project

## Overview

ETodo is a full-stack todo list application: a React frontend, an Express REST API and a MariaDB database, with JWT authentication. Each user has their own private todo list. The whole stack can be started with Docker Compose.

## Features

- User authentication (register, login, JWT)
- CRUD operations for todos (create, read, update, delete)
- User-specific todo lists
- Responsive React frontend
- Error handling and middleware
- Dockerized backend and frontend

## Project Structure

```
E-todo/
│
├── backend/
│   ├── .env.example
│   ├── Dockerfile
│   ├── package.json
│   └── script/
│       └── src/
│           ├── index.js
│           ├── config/
│           │   └── db.js
│           ├── middleware/
│           │   ├── auth.js
│           │   └── errorHandler.js
│           └── routes/
│               ├── auth/
│               │   └── auth.js
│               ├── todos/
│               │   ├── todos.js
│               │   └── todos.query.js
│               └── user/
│                   ├── user.js
│                   └── user.query.js
│
├── frontend/
│   ├── .env.example
│   ├── Dockerfile
│   ├── package.json
│   ├── public/
│   └── src/
│       ├── App.js
│       ├── App.css
│       └── ...
│
├── docker-compose.yml
├── e-todo.sql
└── README.md
```

## Prerequisites

- Docker & Docker Compose
- Node.js
- npm or yarn

## Setup & Usage

### 1. Clone the Repository

```sh
git clone https://github.com/AZ044/E-todo.git
cd E-todo
```

### 2. Environment Variables

Copy the example files and adapt them:

```sh
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
```

#### Backend example (`backend/.env`):
```
DB_HOST=database
DB_USER=youruser
DB_PASSWORD=password_db
DB_NAME=etodo
JWT_SECRET=jwt_token
```

> Use `DB_HOST=database` with Docker Compose (the name of the database service), or `localhost` when running without Docker.
> Always replace `JWT_SECRET` and `DB_PASSWORD` with your own secret values.

#### Frontend example (`frontend/.env`):
```
REACT_APP_API_URL=http://localhost:3001
```

### 3. Database Setup

- The `e-todo.sql` file contains the schema for the MariaDB database.
- Docker Compose will automatically set up the database container.

### 4. Running with Docker Compose

```sh
docker-compose up --build
```

- The backend will be available at `http://localhost:3001`
- The frontend will be available at `http://localhost:3000`

### 5. Running Locally (Without Docker)

#### Backend
```sh
cd backend
npm install
npm start
```

#### Frontend
```sh
cd frontend
npm install
npm start
```

## API

### Auth
- `POST /api/auth/register` — Register a new user
- `POST /api/auth/login` — Login and receive JWT

### Todos
- `GET /api/todos` — Get all todos for the authenticated user
- `POST /api/todos` — Create a new todo
- `PUT /api/todos/:id` — Update a todo
- `DELETE /api/todos/:id` — Delete a todo

### Users
- `GET /api/user/profile` — Get user profile

## Technologies Used
- **Backend:** Node.js, Express, MariaDB, JWT
- **Frontend:** React, JavaScript, CSS, Ant Design
- **DevOps:** Docker, Docker Compose

## Authors
- Matéo Busalli & Hugo Abrino

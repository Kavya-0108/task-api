# Task API — Dockerized CI/CD Pipeline

A simple Node.js/Express REST API for managing tasks, containerized with Docker
and automatically built and pushed to Docker Hub via a GitHub Actions CI/CD pipeline
on every push to `main`.

## Architecture

```
Push to main  -->  GitHub Actions  -->  Build Docker image  -->  Push to Docker Hub
```

## Tech Stack
- **Node.js / Express** — REST API
- **Docker** — containerization (multi-stage build for a lean image)
- **GitHub Actions** — CI/CD pipeline
- **Docker Hub** — image registry

## API Endpoints

| Method | Endpoint      | Description         |
|--------|---------------|----------------------|
| GET    | /health       | Health check         |
| GET    | /tasks        | List all tasks       |
| GET    | /tasks/:id    | Get one task         |
| POST   | /tasks        | Create a task         |
| PUT    | /tasks/:id    | Update a task         |
| DELETE | /tasks/:id    | Delete a task         |

## Run Locally

```bash
npm install
npm start
# API available at http://localhost:3000
```

## Run with Docker

```bash
docker build -t task-api .
docker run -p 3000:3000 task-api
```

Or with Docker Compose:

```bash
docker compose up --build
```

## CI/CD Pipeline

On every push to `main`, GitHub Actions:
1. Checks out the code
2. Logs in to Docker Hub
3. Builds the Docker image
4. Pushes the image tagged as `latest` and with the commit SHA

Pipeline definition: `.github/workflows/docker-ci.yml`

## Setup Instructions

See the accompanying setup guide for exact steps to connect this repo to
GitHub Actions and Docker Hub.

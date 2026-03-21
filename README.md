# Production-Ready DevOps Stack

## Overview

This project is a small DevOps-style containerized stack built with Docker Compose.

It includes:
- an application container based on `traefik/whoami`
- an Nginx reverse proxy
- a PostgreSQL database
- environment variable separation with `.env`
- persistent database storage with Docker volumes
- a custom Docker network for inter-service communication

The goal of this project is to demonstrate practical DevOps fundamentals:
- container orchestration with Docker Compose
- reverse proxy configuration
- service separation
- environment-based configuration
- clean Git history
- production-oriented project structure

## Tech Stack

- Docker
- Docker Compose
- Nginx
- PostgreSQL 15
- Traefik Whoami
- WSL2
- VS Code
- Git / GitHub

## Project Structure

```text
production-ready-devops-stack/
├── docker/
│   └── nginx/
│       └── nginx.conf
├── .env.example
├── .gitignore
├── docker-compose.yml
├── LICENSE
└── README.md
```

## How to Run

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd production-ready-devops-stack
```

### 2. Create environment file

Create a local `.env` file in the project root:

```env
POSTGRES_USER=devops
POSTGRES_PASSWORD=your_password
POSTGRES_DB=appdb
```

You can use `.env.example` as a template.

### 3. Start the stack

```bash
docker compose up -d
```

### 4. Verify running containers

```bash
docker ps
```

### 5. Open in browser

```text
http://localhost:8080
```

## Services

### app
A lightweight demo application based on `traefik/whoami`.

### nginx
Acts as a reverse proxy and forwards incoming requests to the application container.

### postgres
Provides persistent PostgreSQL storage using a named Docker volume.

## Environment Variables

The PostgreSQL service uses environment variables from the local `.env` file:

- `POSTGRES_USER`
- `POSTGRES_PASSWORD`
- `POSTGRES_DB`

The repository includes `.env.example`, while `.env` is ignored via `.gitignore`.

## Current Status

Implemented:
- Docker Compose multi-container setup
- Nginx reverse proxy
- PostgreSQL with persistent volume
- custom Docker network
- `.env`-based configuration
- improved `.gitignore`

## Next Steps

Planned improvements:
- add a real custom application container
- add healthcheck for a suitable service
- create GitHub Actions workflow
- improve documentation
- add infrastructure diagram
- add CI validation for Docker Compose

## Notes

This project is being built step by step as a hands-on DevOps learning and portfolio project.

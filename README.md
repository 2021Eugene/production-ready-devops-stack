# Production-Ready DevOps Stack

[![CI](https://github.com/2021Eugene/production-ready-devops-stack/actions/workflows/ci.yml/badge.svg)](https://github.com/2021Eugene/production-ready-devops-stack/actions/workflows/ci.yml)

## Overview

This project is a small DevOps-style containerized stack built with Docker Compose.

It includes:
- a custom application container built from `docker/app/Dockerfile`
- an Nginx reverse proxy
- a PostgreSQL database
- environment-based configuration using `.env`
- persistent database storage with Docker volumes
- a custom Docker network for inter-service communication
- PostgreSQL healthcheck
- resource limits for services
- GitHub Actions CI validation

The goal of this project is to demonstrate practical DevOps fundamentals:
- container orchestration with Docker Compose
- reverse proxy configuration
- service separation
- environment-based configuration
- Docker image build validation
- healthchecks and service control
- clean Git history
- production-oriented project structure

## Features

- Multi-container Docker Compose setup
- Custom application image build from `docker/app/Dockerfile`
- Nginx reverse proxy for incoming HTTP traffic
- PostgreSQL 15 with persistent named volume
- Environment-based configuration using `.env`
- Custom Docker network for service communication
- PostgreSQL healthcheck with `pg_isready`
- Resource limits for application services
- GitHub Actions CI for Docker Compose validation
- GitHub Actions CI for Docker image build validation

## Tech Stack

- Docker
- Docker Compose
- Nginx
- PostgreSQL 15
- GitHub Actions
- WSL2
- VS Code
- Git / GitHub

## Project Structure

```text
production-ready-devops-stack/
├── .github/
│   └── workflows/
│       └── ci.yml
├── docker/
│   ├── app/
│   │   ├── Dockerfile
│   │   └── index.html
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
git clone https://github.com/2021Eugene/production-ready-devops-stack.git
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
docker compose up --build -d
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
A custom lightweight application container built from `docker/app/Dockerfile`.

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

## Healthcheck

The PostgreSQL service includes a healthcheck using `pg_isready`.

This allows Docker to verify whether the database is ready to accept connections.

## CI

This project includes a GitHub Actions workflow located at:

```text
.github/workflows/ci.yml
```

The CI pipeline currently validates:

- Docker Compose configuration
- Docker image build process

## Current Status

Implemented:

- Docker Compose multi-container setup
- Custom application container
- Nginx reverse proxy
- PostgreSQL with persistent volume
- Custom Docker network
- .env-based configuration
- PostgreSQL healthcheck
- Resource limits
- GitHub Actions CI
- Improved .gitignore
- Project README
- CI status badge

## Next Steps

Planned improvements:

- add Prometheus monitoring
- add Grafana dashboards
- add architecture diagram
- improve production-style documentation
- extend CI pipeline
- add CD workflow
- add container security checks

## Notes

This project is being built step by step as a hands-on DevOps portfolio project.


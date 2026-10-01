# CI/CD Node App

A sample Node.js (Express) app with a GitHub Actions pipeline that tests, builds, and pushes a Docker image to Docker Hub on every push to `main`.

## Pipeline

`push to main` → **test** (Jest) → **build** (Docker) → **push** (Docker Hub)

Defined in `.github/workflows/main.yml`.

## Run locally

```bash
npm install
npm start
```

App runs at http://localhost:3000

Endpoints:
- `/` returns a greeting
- `/health` returns `{"status":"ok"}`

## Run tests

```bash
npm test
```

## Run with Docker

```bash
docker build -t cicd-node-app .
docker run -p 3000:3000 cicd-node-app
```

## Setup CI/CD

Add these secrets in GitHub (Settings → Secrets and variables → Actions):

| Secret | Value |
|---|---|
| `DOCKERHUB_USERNAME` | Your Docker Hub username |
| `DOCKERHUB_TOKEN` | Docker Hub access token |

Then push to `main` and the pipeline runs automatically.

## Tech

GitHub, GitHub Actions, Node.js, Express, Jest, Docker, Docker Hub

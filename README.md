# Containerized NestJS + PostgreSQL API (Docker & CI/CD)

A production-style backend application (NestJS + PostgreSQL) built to practice and demonstrate containerization workflows, local multi-container development, and automated CI/CD pipelines using Docker and GitHub Actions.

## What this project demonstrates

### Docker & Containerization
- **Multi-stage builds** to separate build-time dependencies (TypeScript compiler, dev tooling) from runtime dependencies, keeping the final production image lightweight and secure.
- **Docker Compose** for multi-container local development, configuring services, bind mounts, and persistent volumes.
- **Troubleshooting & Debugging**: Diagnosed and resolved real-world container issues, including inter-container networking, environment variable injection, and dependency version conflicts across build stages.

### CI/CD Automation (GitHub Actions)
- **Automated Build & Push Pipeline**: Configured a GitHub Actions workflow (`.github/workflows/`) that triggers on every code push to automatically build and push Docker images to a private **Docker Hub** registry.
- **Security Best Practices**: Managed sensitive credentials (registry tokens, secrets) securely using **GitHub Secrets**, avoiding hardcoded credentials in the repository.
- **Automated Versioning**: Implemented semantic versioning driven by **Conventional Commits** (`feat:` -> minor, `fix:` -> patch), automatically tagging and publishing new image releases.

## Tech Stack
- **Backend Framework:** NestJS (TypeScript)
- **Database:** PostgreSQL
- **Containerization:** Docker, Docker Compose
- **CI/CD & Automation:** GitHub Actions, Docker Hub

## Running locally

### Prerequisites
- Docker Engine & Docker Compose installed
- Local `.env` file configured (see `.env.example`)

### Development & Production Commands

```bash
# Build & run in Development mode
docker build --target=dev -t docker-graphql:dev .
docker run -p 3000:3000 --env-file .env docker-graphql:dev

# Build & run in Production mode
docker build --target=prod -t docker-graphql:prod .
docker run -p 3000:3000 --env-file .env docker-graphql:prod

# Run full stack with Docker Compose
docker compose up --build
```

## Notes

This project was built as part of hands-on DevOps practice to master containerization and deployment pipelines. It complements an **AWS Certified Solutions Architect – Associate (SAA-C03)** background by showcasing practical application packaging. 

*Future iteration:* Infrastructure deployment via Infrastructure as Code (Terraform) will be hosted in a dedicated cloud repository.

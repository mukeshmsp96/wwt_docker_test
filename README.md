# Mindmeld Devops Take-home Exercise

This exercise is intended to test your knowledge and expertise of devops
tooling and commonly-used AWS products.

In this repository you'll find two directories:

* `api/` -- a simple key-value store API written in Rust
* `app/` -- a simple React frontend to interact with the KV store in a browser

The goal of the exercise is to operate a fully-functioning application stack on
AWS. Availability and resiliency are important, though your implementation does
not need to be overly elaborate. It is more important to demonstrate strong 
principles and opportunities for improvement than it is to build an exhaustive
solution. Be prepared to discuss potential improvements to your solution.

At minimum, you will need to:

* host the API
* host a Redis database for the API to communicate with
* host the frontend application and have it communicate with the API


---
## Quick start (local using Docker Compose)

Requirements: `docker` and `docker compose` installed.

1. From the repository root, build and run:

## Build & push images (example)

Build locally and push to a registry (Docker Hub example):

```bash
docker build -t <your-user>/api:latest ./api
docker build -t <your-user>/app:latest ./app
docker login
docker push <your-user>/api:latest
docker push <your-user>/app:latest
```

For AWS ECR, create repositories and use `aws ecr get-login-password` to authenticate, then tag & push.

---
## CI / CD (summary)

- A provided GitHub Actions workflow builds images and pushes them to Docker Hub using short-lived tags (git SHA).
- Deployment to Kubernetes can be performed by updating image tags in manifests or using `kubectl set image` and `kubectl rollout status`.

See `DEPLOYMENT.md` for the full CI pseudocode (GitHub Actions and Jenkins) and deployment recommendations.

---
If you want, run a local `docker compose build` to validate the images.

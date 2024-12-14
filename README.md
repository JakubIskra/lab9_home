# SW - przekład wykorzystania Github Actions 

Bardzo prosta aplikacja: serwer http ze statyczną stroną www 
Plik "./github/workflows/gha_example.yaml" definiuje:
pipeline GitHub Actions 
- budowanie obrazu multiarch, 
- przesłanie na Dockerhub z nowym tagiem, 
- wykorzystanie cache

Sprawozdanie

Link do Docker Hub - https://hub.docker.com/repository/docker/iskra56/example/general

This repository demonstrates a CI/CD workflow configured with GitHub Actions (GHA). The workflow automates:
1. Building and tagging a Docker image.
2. Running vulnerability tests using Docker Scout.
3. Pushing the image to:
   - DockerHub
   - GitHub Container Registry (GHCR) **only if no critical or high vulnerabilities are found**.

## Configuration Steps

### Workflow Configuration
The workflow performs the following steps:
1. **Checkout the repository**: Fetches the source code.
2. **Build and tag Docker image**: Builds the Docker image using `docker/build-push-action`.
3. **Run vulnerability tests**: Analyzes the image using Docker Scout and ensures no critical/high vulnerabilities exist.
4. **Push to registries**:
   - DockerHub (always)
   - GHCR (only if no critical/high vulnerabilities exist).

### Test Setup
To enable the test:
1. Add the following secrets in your repository settings:
   - `DOCKERHUB_USERNAME`: Your DockerHub username.
   - `DOCKERHUB_TOKEN`: Your DockerHub access token.
   - `GITHUB_TOKEN`: Personal Access Token for GitHub.
   - `GITHUB_USERNAME`: Your GitHub username.
2. The workflow is triggered by pushing a tag

### Output Confirmation
The following logs confirm the workflow's successful execution:
1. **Image built successfully**.
2. **No critical/high vulnerabilities found**.
3. **Image pushed to GHCR**.

# PR Automation Pipeline with GitHub Actions

This project automates the generation of branch-specific Dockerfiles for pull requests (PRs) using GitHub Actions. The goal is to make reviewing PRs easier by containerizing each branch in a Docker environment without affecting the local setup.

## Key Features

- **Automatic Dockerfile Creation**: A branch-specific Dockerfile is generated when a PR is opened.
- **Isolated Environment**: Each branch is containerized, allowing reviewers to test code without affecting their local environment.
- **Artifacts**: The generated Dockerfile is uploaded as an artifact for easy download and use.

## Technologies

- **GitHub Actions**: Automates Dockerfile generation and artifact creation.
- **Docker**: Used to containerize the application for each branch.
- **React**: The core framework for the web application being containerized.

## How It Works

1. A GitHub Actions workflow triggers when a PR is created.
2. The workflow copies a Dockerfile template, replaces the branch name, and builds a Dockerfile for that branch.
3. The Dockerfile is uploaded as an artifact, allowing reviewers to download and run the container.

## Getting Started

To run the Docker container for any PR branch:

1. Clone the repository and check out the branch.
2. Download the Dockerfile artifact generated by GitHub Actions.
3. Build and run the Docker container:
   ```bash
   docker build -f dockerfile.<branch-name> -t <app-name> .
   docker run -p 3300:3300 <app-name>

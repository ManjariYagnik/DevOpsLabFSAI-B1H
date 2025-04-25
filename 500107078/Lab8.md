DevOps Lab 8 – FastAPI Dockerization & CI/CD using GitHub Actions
Name: Manjari Yagnik
SAP ID: 500107078
Roll Number: R2142220568
Program: B.Tech CSE (Full Stack AI) – Honours
College: UPES Dehradun
Lab Title: Automating Docker Builds with GitHub Actions
Repository: [GitHub - Lab 8]

Objective
To containerize a FastAPI application and automate its Docker image build and push process using GitHub Actions, ensuring a seamless CI/CD pipeline for deployment.

Tools & Technologies Used
FastAPI (Python web framework)
Docker / Podman (Container platform)
GitHub Actions (CI/CD platform)
Docker Hub (Image registry)
Git (Version control)
Step 1: Install Podman (Docker Alternative)
Podman is a container engine that can serve as a replacement for Docker.

Installation
Download podman-cli from https://podman.io
Initialize Podman machine and configure alias:
podman machine init
podman machine start
alias docker=podman
docker --version
Step 2: FastAPI Server Code
File: main.py

from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/")
def root():
    return {"name": "Jaanhvi", "Location": "Dehradun"}

@app.get("/{data}")
def dynamic(data: str):
    return {"hi": data, "Location": "Dehradun"}

if __name__ == "__main__":
    uvicorn.run("main:app", host="0.0.0.0", port=80, reload=True)
Step 3: Requirements
File: requirements.txt

fastapi
uvicorn
Step 4: Dockerfile
File: Dockerfile

FROM ubuntu

RUN apt update -y && apt install -y python3 python3-pip pipenv

WORKDIR /app
COPY . /app/
RUN pipenv install -r requirements.txt

EXPOSE 80
CMD pipenv run python3 ./main.py
Step 5: Build and Run (Manual)
Build Image
docker build -t fastapi-jaanhvi:v1 .
List Images
docker images
Run Container
docker run fastapi-jaanhvi:v1
Step 6: GitHub Actions Workflow
File: .github/workflows/DockerBuild.yml

name: Docker image build

on: push

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: Build & Push Image
        run: |
          echo ${{ secrets.DOCKERTOKEN }} | docker login -u "jaanhvisaxena" --password-stdin
          docker build -t jaanhvisaxena/fastapi-docker:v0.1 .
          docker push jaanhvisaxena/fastapi-docker:v0.1
Docker Token Setup
Steps:
Visit Docker Hub
Go to Account Settings > Security > Access Tokens
Generate a token, give it a name, set permissions
Copy and store it securely (you’ll use this in GitHub Secrets)
Login using token:

echo "<your-token>" | docker login -u <your-username> --password-stdin
Workflow Explanation
Trigger: The workflow runs on every push to the repo.
Steps:
Checkout code from GitHub
Log in to Docker Hub using stored secrets
Build the Docker image
Push the image to Docker Hub
Outcome
This GitHub Actions workflow automates:

Building the Docker image
Logging into Docker Hub
Pushing the image
This ensures a faster, more consistent, and automated deployment process for your containerized FastAPI application.

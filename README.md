DevOps Internship Day -1
Task -1
🚀 Node.js CI/CD Pipeline using GitHub Actions & Docker

This project demonstrates how to automate the build and deployment of a simple Node.js web application using GitHub Actions and DockerHub.

📁 Repository Structure
├── .github
│   └── workflows
│       └── main.yml      # CI/CD Workflow file
├── Dockerfile            # Docker build configuration
├── package.json
├── index.js
└── README.md             # Project documentation

🎯 Objective

Set up a CI/CD pipeline that:

Installs dependencies

Runs unit tests

Builds a Docker image

Pushes the image to DockerHub automatically on every push to the main branch

🛠️ Setup Instructions

✅ Step 1: Fork the Repo

Fork this repo: nodejs-demo-app

✅ Step 2: Create GitHub Actions Workflow

Create .github/workflows/main.yml and add the following:

name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

  docker:
    needs: build
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Log in to DockerHub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}

      - name: Build Docker image
        run: docker build -t ${{ secrets.DOCKER_USERNAME }}/nodejs-demo-app .

      - name: Push Docker image
        run: docker push ${{ secrets.DOCKER_USERNAME }}/nodejs-demo-app

✅ Step 3: Add Dockerfile

FROM node:16

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]

✅ Step 4: Add GitHub Secrets

Go to:
GitHub Repo → Settings → Secrets → Actions → New repository secret

Add:

DOCKER_USERNAME

DOCKER_PASSWORD (or Docker Access Token)

✅ Step 5: Commit and Push
![image](https://github.com/user-attachments/assets/ebc82960-7389-4e93-aa9a-e55661cfcff9)




🚀 Node.js CI/CD Pipeline with Docker & GitHub Actions

This project demonstrates a simple Node.js application with a full CI/CD pipeline using GitHub Actions and Docker.

🧰 Tech Stack

Node.js – Lightweight HTTP server
Docker – Containerize the app
GitHub Actions – CI/CD automation
DockerHub – Host and pull images
📦 Setup Instructions

1️⃣ Clone the Repository

git clone https://github.com/mohammed-saifuddin/ci-cd-nodejs-app.git
cd ci-cd-nodejs-app
2️⃣ Install Dependencies

npm install
3️⃣ Run the App Locally

node index.js
App will run on http://localhost:3000

🧪 Run Tests

npm test
🐳 Docker Commands

🔨 Build Docker Image

docker build -t mohammed-saifuddin/ci-cd-nodejs-app .
▶️ Run Docker Container

docker run -p 3000:3000 mohammed-saifuddin/ci-cd-nodejs-app
📤 Push to DockerHub

docker push mohammed-saifuddin/ci-cd-nodejs-app
🔄 GitHub Actions: CI/CD Flow

Whenever you push to the main branch:

GitHub Actions will:
Checkout the code
Set up Node.js
Install dependencies
Run tests
Build Docker image
Login to DockerHub
Push Docker image to DockerHub
📂 Project Structure

. ├── .github/ │ └── workflows/ │ └── main.yml # GitHub Actions CI/CD workflow ├── Dockerfile # Docker configuration ├── index.js # Main Node.js server ├── package.json # Dependencies and scripts └── README.txt # Project documentation


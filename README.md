
# 🚀 Docker Experiments - 500094696

This repository contains three experiments demonstrating how to containerize and run Python and Streamlit applications using Docker. Each experiment serves a different purpose — from running a basic Python script to deploying a Streamlit-based machine learning application.

---

## 🧪 Experiments Overview

### **📁 `exp1/` — Basic Python Script in Docker**
- Demonstrates how to run a simple Python script (`app.py`) inside a Docker container.
- Good starting point for learning Docker with Python.

### **📁 `exp2/` — Streamlit App via Git Repo in Docker**
- Clones the official [Streamlit example app](https://github.com/streamlit/streamlit-example) inside the container.
- Installs system and Python dependencies.
- Runs the Streamlit app on port `8501`.
- Includes a health check for container monitoring.

### **📁 `exp3/` — ML Model Deployment Using Streamlit**
- Deploys a local machine learning Streamlit app (`app.py`) using Docker.
- Includes `requirements.txt` and dataset (`mushrooms.csv`).
- Showcases how to containerize and expose an ML-based dashboard.

---

## 🐳 Getting Started with Docker

### **🛠 Prerequisites**
- Install [Docker](https://docs.docker.com/get-docker/)

---

## 🚨 How to Run Each Experiment

### 🔹 Experiment 1 — Run a Basic Python Script

bash
cd exp1
docker build -t python-script .
docker run python-script


---

### 🔹 Experiment 2 — Run a Streamlit App from GitHub

bash
cd exp2
docker build -t streamlit-demo .
docker run -p 8501:8501 streamlit-demo


- Open [http://localhost:8501](http://localhost:8501) in your browser.

---

### 🔹 Experiment 3 — Deploy a Streamlit ML App

bash
cd exp3
docker build -t ml-streamlit-app .
docker run -p 8501:8501 ml-streamlit-app


- Visit [http://localhost:8501](http://localhost:8501) to interact with the model.

---

## 📄 Folder Structure


├── exp1
│   ├── Dockerfile
│   └── app.py
├── exp2
│   └── Dockerfile
├── exp3
│   ├── Dockerfile
│   ├── app.py
│   ├── mushrooms.csv
│   └── requirements.txt


---

## 🧼 Cleaning Up

To remove all containers and images after you're done:

bash
docker container prune
docker image prune -a


---

## 📢 License

This project is licensed under the MIT License.

---

Happy Containerizing! 🐋

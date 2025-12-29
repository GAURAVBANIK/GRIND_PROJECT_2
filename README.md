# Dockerized Django 3-Tier Application

This project demonstrates a production-style **3-tier Docker architecture** using:

- **Django** (Application Layer)
- **PostgreSQL** (Database Layer)
- **NGINX** (Reverse Proxy & Static Files)

The goal of this project was to practice real-world Docker and Docker Compose workflows rather than just running Django locally.

---

## 🏗 Architecture Overview

Browser
↓
NGINX (port 80)
↓
Django (port 8000)
↓
PostgreSQL (port 5432)

yaml
Copy code

---

## 🚀 Tech Stack

- Python 3.13
- Django 6.0
- PostgreSQL 16
- NGINX (Alpine)
- Docker & Docker Compose

---

## 📂 Project Structure

.
├── docker-compose.yml
├── Dockerfile
├── nginx/
│ └── nginx.conf
├── src/ # Django source code
├── public_collected/ # Collected static files
├── .env.example
├── pyproject.toml
└── uv.lock

yaml
Copy code

---

## ⚙️ How to Run

```bash
cp .env.example .env
docker compose up --build
Then open:

👉 http://localhost:8000 (Django)

👉 http://localhost (via NGINX)

🧠 What I Learned (Important)
Initially, I assumed the project was using MySQL

After debugging connection and driver errors, I discovered the app was actually configured for PostgreSQL

This required:

Updating docker-compose.yml

Switching database service to PostgreSQL

Rebuilding images

Installing the correct database driver:

bash
Copy code
pip install psycopg
I also learned how Django behaves differently with static files in Docker and why NGINX is required in production setups

This experience helped me understand how real production debugging works instead of following tutorials blindly.

✅ Key Docker Concepts Practiced
Multi-service Docker Compose

Health checks & service dependencies

Environment variables with .env

Database driver compatibility issues

Rebuilding images after dependency changes

Separating application & infrastructure concerns

👤 Author
Gaurav Banik

yaml
Copy code

---

## ✅ Final checklist before push

Run these once:

```bash
git status
git add .
git commit -m "Dockerized Django app with PostgreSQL and NGINX"
git push origin main

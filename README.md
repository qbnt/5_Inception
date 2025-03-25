# Inception

`Inception` is a 42 project designed to strengthen your understanding of system virtualization by using Docker. The goal is to set up a full infrastructure of containers and services within a personal virtual machine.

## 🛠️ Project Overview

The project consists of creating several Docker images and running them in containers. These containers together simulate a basic server environment, offering services like a website, database, FTP, and more. Everything must be orchestrated securely and automatically.

## 🧱 Infrastructure Requirements

You will need to set up and containerize services such as:

- **Nginx** — reverse proxy with SSL support
- **WordPress** — content management system
- **MariaDB** — database service for WordPress

Each service must run in its own container and communicate over a private Docker network.

## 🧰 Tools & Technologies

- Docker
- Docker Compose
- Bash scripting
- Environment variables (.env)
- SSL certificates (self-signed)
- Volumes and persistent storage

## 🔧 Installation

1. Clone the repository:

```bash
git clone https://github.com/qbnt/5_Inception.git
cd 4_Inception
```

2. Create your `.env` file and adjust configurations.

3. Build and start the containers:

```bash
docker-compose up --build
```

## 📦 File Structure

```
inception/
├── srcs/
│   ├── requirements/
│   │   ├── nginx/
│   │   ├── wordpress/
│   │   ├── mariadb/
│   ├── docker-compose.yml
│   └── .env
├── Makefile
└── README.md
```

## ✅ Objectives

- Understand containerization and service isolation
- Automate multi-service infrastructure deployment
- Secure services with HTTPS and proper user permissions
- Persist data using Docker volumes

## 📌 Notes

- The use of Docker Desktop is not allowed.
- Everything must be run in your own Linux VM (e.g., Debian/Ubuntu).
- The project must follow 42's Norms for structure and code cleanliness.


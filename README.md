# 🌩️ Cloud-Enabled Deployment with **AWS** & **GCP**

A **cloud-ready microservices application** demonstrating full-stack development with **local development** and **cloud deployment** support.

### 🔹 Key Projects in this Repository

| Project                | Description                                | Tech Stack                             |
| ---------------------- | ------------------------------------------ | -------------------------------------- |
| 📘 **course-service**  | Manages courses                            | Spring Boot + MySQL                    |
| 🎓 **student-service** | Manages student data                       | Spring Boot + MongoDB                  |
| 🗂️ **media-service**  | Handles file storage       | Spring Boot + Local Storage |
| 💻 **frontend-app**    | User interface for Courses, Students, Media | React + TypeScript + Vite              |

---

<p align="center">
  <a href="https://drive.google.com/file/d/1_8cZFj6s3nJ5NYVW0jUezo-OADNyMfED/view?usp=sharing" target="_blank">
    <img src="https://img.shields.io/badge/Watch_Demo-4CAF50?style=for-the-badge&logo=google-drive&logoColor=white" alt="Watch Demo"/>
  </a>
</p>

---

<p align="center">
  <a href="https://www.java.com/" target="_blank"><img src="https://img.shields.io/badge/Java-000000?style=for-the-badge&logo=openjdk&logoColor=white"></a>
  <a href="https://spring.io/projects/spring-boot" target="_blank"><img src="https://img.shields.io/badge/SpringBoot-000000?style=for-the-badge&logo=springboot&logoColor=white"></a>
  <a href="https://www.mysql.com/" target="_blank"><img src="https://img.shields.io/badge/MySQL-000000?style=for-the-badge&logo=mysql&logoColor=white"></a>
  <a href="https://www.mongodb.com/" target="_blank"><img src="https://img.shields.io/badge/MongoDB-000000?style=for-the-badge&logo=mongodb&logoColor=white"></a>
  <a href="https://react.dev/" target="_blank"><img src="https://img.shields.io/badge/React-000000?style=for-the-badge&logo=react&logoColor=white"></a>
  <a href="https://www.typescriptlang.org/" target="_blank"><img src="https://img.shields.io/badge/TypeScript-000000?style=for-the-badge&logo=typescript&logoColor=white"></a>
  <a href="https://vitejs.dev/" target="_blank"><img src="https://img.shields.io/badge/Vite-000000?style=for-the-badge&logo=vite&logoColor=white"></a>
  <a href="https://www.docker.com/" target="_blank"><img src="https://img.shields.io/badge/Docker-000000?style=for-the-badge&logo=docker&logoColor=white"></a>
  <a href="https://aws.amazon.com/" target="_blank"><img src="https://img.shields.io/badge/AWS-000000?style=for-the-badge&logo=amazonaws&logoColor=white"></a>
  <a href="https://cloud.google.com/" target="_blank"><img src="https://img.shields.io/badge/GCP-000000?style=for-the-badge&logo=googlecloud&logoColor=white"></a>
</p>

---

## 📌 Backend Services

### 1. Course Service

* **Entity:** `Course(id, name, duration)`
* **Endpoints:**

    * `GET /courses`
    * `GET /courses/{id}`
    * `POST /courses`
    * `DELETE /courses/{id}`
* **Default Port:** `8081`
* **Profiles:**

    * `dev` → MySQL in Docker
    * `aws` → AWS RDS MySQL
    * `gcp` → GCP Cloud SQL (MySQL)

---

### 2. Student Service

* **Document:** `Student(registrationNumber, fullName, address, contact, email)`
* **Endpoints:**

    * `GET /students`
    * `GET /students/{id}`
    * `POST /students`
    * `DELETE /students/{id}`
* **Default Port:** `8082`

---

### 3. Media Service

* **Resource:** `files`
* **Endpoints:**

    * `POST /files` – Upload file (`multipart/form-data`)
    * `GET /files` – List files
    * `GET /files/{id}` – Fetch file
    * `DELETE /files/{id}` – Delete file
* **Default Port:** `8083`
* **Storage:** Local disk at `./data/media` (override with `MEDIA_STORAGE_DIR`)

---

## 🎨 Frontend (frontend-app)

* Built with **React + TypeScript + Vite + MUI + Axios**
* Provides UI for: Courses, Students, Media
* **Scripts:**

    * `npm run dev` → Start Vite dev server
    * `npm run build` → Build app (TypeScript + Vite)

---

## ⚙️ Development Environment

In **development mode**:

* **MySQL** and **MongoDB** run inside Docker containers with persistent volumes.
* Backend services are started using the `dev` profile.

### Start MySQL (with volume)

```bash

docker run -d \
  --name mysql-dev \
  -e MYSQL_ROOT_PASSWORD=mysql \
  -p 15000:3306 \
  -v mysql-data:/var/lib/mysql \
  mysql:lts
```

### Start MongoDB (with volume)

```bash

docker run -d \
  --name mongo-dev \
  -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=mongo
  -p 16000:27017 \
  -v mongo-data:/data/db \
  mongo:7.0.23
```

Both containers will persist data in their respective Docker volumes (`mysql-data`, `mongo-data`).

---

## ☁️ Cloud Profiles (Course Service Only)

The `course-service` supports cloud profiles for connecting to external MySQL databases:

* **AWS Profile** (`aws`) → Connects to **AWS RDS (MySQL)**

    * Configure credentials in `application-aws.properties`
    * 📺 [Watch: How to create a MySQL DB in AWS RDS](https://youtu.be/3lRoZ-b2A04?si=ctReXSdGcdnIZDvw)

* **GCP Profile** (`gcp`) → Connects to **Google Cloud SQL (MySQL)**

    * Configure credentials in `application-gcp.properties`
    * 📺 [Watch: How to create a MySQL DB in GCP Cloud SQL](https://youtu.be/0K7LpX-jrGY?si=9Se4fB9mqGmB7Yjt)

---

## 🚀 Running the Application

1. Start the **backend services**:

    * `course-service` → run with the correct profile (`dev`, `aws`, or `gcp`)
    * `student-service`
    * `media-service`


2. Start the **frontend app** (`frontend-app`).
* In **dev mode** → Uses Dockerized MySQL & MongoDB.
* In **cloud mode** → `course-service` connects to **AWS RDS** (`aws`) or **GCP Cloud SQL** (`gcp`).

---

## 📄 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  &copy; 2025 Janindu Lokitha <br/>
  Licensed under the <a href="LICENSE">MIT License</a>
</p>  

---

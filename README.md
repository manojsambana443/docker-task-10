# DevOps Internship – Task 10: Docker Volumes & Networking

## 📌 Task Objective

The objective of this task is to understand how Docker handles **data persistence** using volumes and how **container-to-container communication** works using custom Docker networks. This task demonstrates why volumes and networks are essential in real-world containerized applications.

---

## 🛠 Tools Used

* Docker (CLI)
* OS: Linux

---

## 📂 Architecture Overview

This setup consists of:

* A **Docker Host** (local machine)
* A **Docker Volume** (`mydata`) to persist application data
* A **Custom Docker Bridge Network** (`mynetwork`) for container communication
* Multiple containers connected via volumes and network

The architecture diagram is included in the `screenshots/architecture.png` file.

---

## 📦 Part 1: Docker Volumes (Data Persistence)

### Why Docker Volumes?

Containers are ephemeral by nature, meaning data inside a container is lost when the container is removed. Docker volumes store data outside the container lifecycle, ensuring persistence.

### Steps Performed

1. Created a Docker volume named `mydata`
2. Launched an Nginx container (`web1`) with the volume mounted
3. Stored application data inside the mounted volume
4. Removed the container
5. Created a new container (`web2`) using the same volume
6. Verified that the data persisted

### Proof of Persistence

Even after deleting the original container, the data stored inside the Docker volume remained available in the new container. Screenshots are provided in the `screenshots/` folder.

---

## 🌐 Part 2: Docker Networking (Container Communication)

### Why Docker Networks?

Docker networks allow containers to communicate securely and efficiently without exposing services to the host or external network.

### Steps Performed

1. Created a custom bridge network named `mynetwork`
2. Launched two containers (`app1` and `app2`) inside the same network
3. Assigned network aliases
4. Tested container-to-container communication using `ping`

### Communication Result

Containers successfully communicated with each other using container names, proving internal DNS resolution within the Docker network.

---

## 🔍 Inspection & Verification

The following Docker inspection commands were used to verify the setup:

* `docker volume inspect mydata`
* `docker network inspect mynetwork`

These confirm correct volume attachment and network connectivity.

---

## 📁 Repository Structure

```
docker-task-10/
│
├── screenshots/
│   ├── volume-ls.png
│   ├── container-volume.png
│   ├── persistence-proof.png
│   ├── network-ls.png
│   ├── ping-test.png
│   ├── inspect-volume.png
│   ├── inspect-network.png
│   └── architecture.png
│
└── README.md

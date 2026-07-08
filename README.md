# 🐳 Docker Installation and Networking on AWS EC2

<p align="center">
  <img src="https://img.shields.io/badge/AWS-EC2-orange?logo=amazon-aws" />
  <img src="https://img.shields.io/badge/Docker-Engine-blue?logo=docker" />
  <img src="https://img.shields.io/badge/OS-Ubuntu%20Server-E95420?logo=ubuntu" />
  <img src="https://img.shields.io/badge/Status-Completed-success" />
</p>

## 📌 Objective

This lab demonstrates a complete hands-on walkthrough of setting up **Docker** on an **AWS EC2 (Ubuntu Server)** instance and exploring how Docker's core networking models behave in practice.

The lab covers:

- ✅ Docker installation on AWS EC2
- ✅ Docker configuration for a non-root user
- ✅ Running the `hello-world` container
- ✅ Understanding and testing Docker network types:
  - Bridge Network
  - Host Network
  - None Network
  - Custom Bridge Network

---

## 🖥️ Environment

| Component | Details |
|---|---|
| Cloud Provider | AWS EC2 |
| OS | Ubuntu Server |
| Container Runtime | Docker Engine |

---

## 🚀 What Was Done

### 1️⃣ Docker Installation
Docker Engine was installed on the EC2 instance, verified via version check, and confirmed running as an active system service.

### 2️⃣ Non-Root User Configuration
The `ubuntu` user was added to the `docker` group, removing the need to prefix every command with `sudo` — a standard best practice for smoother Docker workflows.

### 3️⃣ Hello World Verification
The official `hello-world` image was pulled and run to confirm Docker was installed and functioning correctly end-to-end (pull → create → run → output).

---

## 🌐 Docker Networking Explored

### 1. Bridge Network (Default)
Docker's default network driver. Containers get their own private IP and can talk to each other, but stay isolated from the host unless ports are published.

### 2. Host Network
The container shares the host machine's network stack directly — no isolation, no port mapping needed. Fastest, least isolated option.

### 3. None Network
Networking is fully disabled. The container only has a loopback interface — confirmed by a failed `apt update` due to no DNS/internet access.

### 4. Custom Bridge Network
A user-defined bridge network was created, and two containers were connected to it. Unlike the default bridge, custom bridge networks support **automatic DNS resolution by container name** — verified by successfully pinging one container from another using its name.

---

## 📊 Observation Summary

| Network Type | Internet Access | Container-to-Container by Name | Isolation from Host |
|---|:---:|:---:|:---:|
| Bridge (default) | ✅ | ❌ (IP only) | ✅ |
| Host | ✅ | N/A | ❌ |
| None | ❌ | ❌ | ✅ (fully isolated) |
| Custom Bridge | ✅ | ✅ | ✅ |

---

## 📷 Screenshots

All supporting screenshots for each step are available in:

```
screenshots/
```

## 💻 Commands Reference

All shell commands used in this lab are documented separately in:

```
command.md
```

---

## ✅ Assignment Result

| Task | Status |
|---|:---:|
| Docker Installed Successfully | ✅ |
| Non-root User Configured | ✅ |
| Hello World Executed | ✅ |
| Bridge Network Demonstrated | ✅ |
| Host Network Demonstrated | ✅ |
| None Network Demonstrated | ✅ |
| Custom Bridge Network Demonstrated | ✅ |
| Container-to-Container Communication Verified | ✅ |

---

## 👤 Author

**MD. EBNUL AHSAN**

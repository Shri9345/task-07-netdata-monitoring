# 🖥️ Task 07: Monitor System Resources using Netdata

## ✅ Objective:
To install and configure Netdata using Docker on an EC2 Ubuntu 22.04 instance, and monitor real-time system and container performance.

---

## 🧰 Tools Used:
- Netdata (via Docker)
- AWS EC2 Ubuntu 22.04 LTS
- Docker

---

## 🖥️ Setup Steps:

### 1. Installed Docker:
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
newgrp docker

## Netdata Container:
sudo docker run -d --name=netdata \
  -p 19999:19999 \
  --cap-add=SYS_PTRACE \
  --security-opt apparmor=unconfined \
  --restart unless-stopped \
  netdata/netdata

## Accessed Dashboard:
http://<ec2-public-ip>:19999


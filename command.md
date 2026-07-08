# Docker Installation and Networking Lab Commands

## System Update

```bash
sudo apt update
sudo apt upgrade -y
```

## Docker Installation

```bash
sudo apt install docker.io -y
docker --version
sudo systemctl status docker
sudo systemctl enable docker
```

## Configure Docker for Non-Root User

```bash
sudo groupadd docker
sudo usermod -aG docker ubuntu
newgrp docker
groups
```

## Hello World Container

```bash
docker run hello-world
docker ps
```

---

# Docker Networking

## List Docker Networks

```bash
docker network ls
```

---

## Bridge Network

```bash
docker network inspect bridge

docker run -dit --name bridge-container nginx

docker ps

docker inspect bridge-container | grep NetworkMode
```

---

## Host Network

```bash
docker run -d --network host --name host-nginx nginx

docker ps

docker inspect host-nginx | grep NetworkMode

curl http://localhost
```

---

## None Network

```bash
docker run -dit --network none --name none-container ubuntu bash

docker inspect none-container | grep NetworkMode

docker exec -it none-container bash

apt update

exit
```

---

## Custom Bridge Network

```bash
docker network create custom-bridge

docker network ls

docker run -dit --name container1 --network custom-bridge ubuntu bash

docker run -dit --name container2 --network custom-bridge ubuntu bash

docker network inspect custom-bridge

docker exec -it container1 bash

apt update

apt install iputils-ping -y

ping container2

exit

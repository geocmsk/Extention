# Extention Setup VPS 


## Requirements : 


Recommended : 

- 2+ CPU  / 6+ GB RAM / 8+ MBit/sec

#### Run the following command to update and upgrade system packages:

```bash
sudo apt update -y && sudo apt upgrade -y
```
## 2. Install the necessary packages :

```bash
sudo apt install htop ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev tmux iptables curl nvme-cli git wget make jq libleveldb-dev build-essential pkg-config ncdu tar clang bsdmainutils lsb-release libssl-dev libreadline-dev libffi-dev jq gcc screen unzip lz4 -y
```
## 3. Install Docker : 

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
docker version
```

## 4. Install Docker Compose : 

```bash
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)
curl -L "https://github.com/docker/compose/releases/download/$VER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## 4. Docker User Permissions

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

## Let's learn the time zone ; 

```bash
realpath --relative-to /usr/share/zoneinfo /etc/localtime
```

- Save Time Zone

## Install Chromium ; 

```bash
mkdir chromium
cd chromium
```

## Create Docker Compose File ; 

```bash
nano docker-compose.yaml
```

## Places we will change ; 

- User
- Password
- TZ

```bash
---
services:
  chromium:
    image: lscr.io/linuxserver/chromium:latest
    container_name: chromium
    security_opt:
      - seccomp:unconfined #optional
    environment:
      - CUSTOM_USER=username
      - PASSWORD=password
      - PUID=1000
      - PGID=1000
      - TZ=Europe/London
      - CHROME_CLI=https://github.com/FurkanL0 #optional
    volumes:
      - /root/chromium/config:/config
    ports:
      - 3010:3000   #Change 3010 to your favorite port if needed
      - 3011:3001   #Change 3011 to your favorite port if needed
    shm_size: "4gb"
    restart: unless-stopped
```

- Example ; 

![resim](https://github.com/user-attachments/assets/d52d9302-dbb8-47a6-93ab-74b5a82cab16)


## CTRL X CTRL Y Enter Saved.

## Let's Start the Server Chromium ; 
```bash
cd $HOME && cd chromium
```
```bash
docker compose up -d
```

- Access Our Server ; 

```bash
http://server-ip:3010/
https://server-ip:3011/
```

- Enter the Username - Password you have set.


![resim](https://github.com/user-attachments/assets/88e6b139-b364-4c42-bd5f-653547b29bc5)

- After that, you can download plugins and log in via chromium as if you are connected to the Windows server.

![resim](https://github.com/user-attachments/assets/84930d45-62e6-484c-8465-880c35a9228b)

## Projects : 

- LayerEdge : https://x.com/FurkanL0eth/status/1882341359199072508 - Link : https://dashboard.layeredge.io
🥷Code : u6UQwxO1

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=FurkanL0&style=flat-square&color=brightgreen&label=Profile+Views+/+Repo+Views+" alt="Repo / Profile Views" />
</p>



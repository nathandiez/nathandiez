
Setting up IoT Service with Docker on GCP Debian Server

Log into GC ssh browser session
sudo su

passwd nathan

passwd eric

Time Zone Setup
sudo timedatectl set-timezone America/New_York
timedatectl  # verify
add users to docker group and create it
sudo groupadd docker
sudo usermod -aG docker eric 
sudo usermod -aG docker nathan
Switch to a new user session with both

sudo su - eric 
sudo su - nathan
exec su -l $USER

Installation Steps
1. Install Docker and Docker Compose
Connect to your Debian server via SSH and run:
# Install Docker
sudo apt-get update
sudo apt-get install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

# Install Docker Compose
sudo apt-get install docker-compose -y
docker-compose --version

Directory Setup:
Bash

mkdir -p $HOME/eiotservice/{web,data,logs}
cd $HOME/eiotservice
Create .env:
Bash
touch $HOME/eiotservice/.env
# Add environment variables to .env as needed (KEY=value format)
Create docker-compose.yml:
Bash
nano $HOME/eiotservice/docker-compose.yml  # Paste the corrected YAML.
Create docker-compose.yaml with the following content:
version: '3.8'
services:
  iot-app:
    image: nathandiez12/eiotservice:latest
    container_name: eiotservice
    restart: unless-stopped
    logging:
      driver: json-file
      options:
        max-size: 10m
        max-file: "3"
    environment:
      TZ: America/New_York
    env_file:
      - .env  # Relative path!
    volumes:
      - ./web:/app/web
      - ./data:/app/data
      - ./logs:/app/logs
    networks:
      - iot-network
  apache-web:
    image: httpd:latest
    ports:
      - "80:80"
    volumes:
      - ./web:/usr/local/apache2/htdocs:ro
    networks:
      - iot-network
    depends_on:
      - iot-app
  grafana:
    image: grafana/grafana:latest
    container_name: grafana
    restart: unless-stopped
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=admin
      - GF_USERS_ALLOW_SIGN_UP=false
    volumes:
      - grafana_data:/var/lib/grafana
    networks:
      - iot-network

volumes:
  grafana_data:
networks:
  iot-network:
    driver: bridge
Bash
cd $HOME/eiotservice
docker-compose up -d
Verify:
docker ps
docker logs eiotservice (and other container names)
Access Apache and cAdvisor via browser.
Create docker-compose.yaml with the following content:7. Verification Steps
Check container status:
docker-compose ps


Verify group setup:
getent group eiotadmin
groups eric
groups nathan
Docker Commands Reference
docker ps                           # Container status
docker stop eiotservice            # Stop container
docker rm -f eiotservice          # Remove container
docker logs -f eiotservice        # View logs
docker inspect eiotservice        # Container details
docker stats eiotservice         # Container statistics
docker exec -it eiotservice /bin/bash  # Interactive shell

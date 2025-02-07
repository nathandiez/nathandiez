Here's the guide, neatly formatted for clarity:

---

# **Setting up IoT Service with Docker on GCP Debian Server**

---

## **1. Log into GCP SSH Browser Session**
```bash
sudo su
```

Change passwords for the users:
```bash
passwd nathan
passwd eric
```

---

## **2. Set Time Zone**
```bash
sudo timedatectl set-timezone America/New_York
timedatectl  # Verify the timezone setup
```

---

## **3. Add Users to Docker Group**
Create the Docker group and add users to it:
```bash
sudo groupadd docker
sudo usermod -aG docker eric 
sudo usermod -aG docker nathan
```

Switch to new user sessions:
```bash
sudo su - eric 
sudo su - nathan
exec su -l $USER
```

---

## **4. Install Docker and Docker Compose**
### **Install Docker**
```bash
sudo apt-get update
sudo apt-get install docker.io -y

# Start and enable Docker service
sudo systemctl start docker
sudo systemctl enable docker
```

### **Install Docker Compose**
```bash
sudo apt-get install docker-compose -y
docker-compose --version  # Verify the installation
```

---

## **5. Create Directory Structure**
```bash
mkdir -p $HOME/eiotservice/{web,data,logs}
cd $HOME/eiotservice
```

---

## **6. Create and Configure .env File**
Create the `.env` file:
```bash
touch $HOME/eiotservice/.env
```
*Add environment variables as needed in the following format:*
```
KEY=value
```

---

## **7. Create docker-compose.yml**
Create the file using:
```bash
nano $HOME/eiotservice/docker-compose.yml
```

### **Paste the following content:**
```yaml
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
      - .env  # Relative path
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
```

---

## **8. Start Docker Services**
Navigate to the project directory and run:
```bash
cd $HOME/eiotservice
docker-compose up -d
```

---

## **9. Verification Steps**
### **Check Running Containers**
```bash
docker ps
```

### **View Logs**
```bash
docker logs eiotservice  # or any other container
```

### **Verify Web Services**
- Access Apache on `http://<server-ip>`
- Access Grafana on `http://<server-ip>:3000`

---

## **10. Verify Group Setup**
```bash
getent group docker
groups eric
groups nathan
```

---

## **Docker Commands Reference**
| **Command**                          | **Description**                        |
|-------------------------------------|----------------------------------------|
| `docker ps`                         | View running containers               |
| `docker stop eiotservice`           | Stop the container                    |
| `docker rm -f eiotservice`          | Remove the container                  |
| `docker logs -f eiotservice`        | View container logs                   |
| `docker inspect eiotservice`        | View container details                |
| `docker stats eiotservice`          | Monitor container resource usage      |
| `docker exec -it eiotservice /bin/bash` | Interactive shell access to the container |

---

This should give you a clean and well-structured setup experience for your IoT project on GCP.

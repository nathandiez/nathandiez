## Featured Projects
Live Dashboard (Azure Open Source Stack): http://74.235.232.127:3000/d/10711dc4-f67e-41ba-af3a-89801da2e582/iot-monitoring 
Username: iots6 | Password: iots6
### Home IoT Monitoring System - Azure Stack

Built a complete IoT system that collects sensor data from custom Raspberry Pi Pico W devices and processes it through Azure cloud services. The project demonstrates practical cloud infrastructure management and real-time data processing. I split the work into two repositories - one for the Azure backend and one for the sensor firmware.

**Technologies:** Azure App Service, Terraform, Azure Data Lake, Databricks, C# .NET, MicroPython, Raspberry Pi Pico W, Azure Key Vault

#### What I Built:
- Azure cloud infrastructure using Terraform for consistent deployments
- RESTful API in C# .NET deployed to Azure App Service for data ingestion
- Automated data storage pipeline to Azure Data Lake with structured folder organization
- Databricks workspace for data analysis with custom Python notebooks
- MicroPython firmware for Pico W with temperature and humidity sensors

**Links:**
- [IoT Backend Repo](https://github.com/nathandiez/iots6_net)
- [IoT Sensor Repo](https://github.com/nathandiez/picosensor_net)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture.md)


### Home IoT Monitoring System - Proxmox/Open Source Stack
Designed and deployed a complete self-hosted IoT platform using open-source technologies on Proxmox virtual infrastructure. Showcases skills in infrastructure automation, container orchestration, and embedded systems programming. I split the work into three repositories - one for the IoT backend, one for the sensor firmware, and one for the configuration server.

**Technologies:** Proxmox, Docker, TimescaleDB, Mosquitto MQTT, Flask, Ansible, Terraform, MicroPython, Raspberry Pi Pico W

#### What I Built:
- Proxmox virtual infrastructure using Terraform for automated VM provisioning and management
- TimescaleDB hypertable database with custom schema for time-series sensor data storage
- Mosquitto MQTT broker with Docker containerization for real-time message processing
- Python data ingestion service that processes MQTT messages and stores to PostgreSQL
- Flask configuration server with Docker deployment and Ansible automation
- Comprehensive monitoring and logging with Docker container orchestration
- MicroPython firmware for Pico W with temperature and humidity sensors

**Links:**
- [IoT Backend Repo](https://github.com/nathandiez/iots6)
- [IoT Sensor Repo](https://github.com/nathandiez/picosensor_net) 
- [Config Server](https://github.com/nathandiez/prox_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture2.md)


### Home IoT Monitoring System - Azure Open Source Stack
Built a hybrid cloud IoT platform that combines Azure infrastructure with open-source technologies, demonstrating cost-effective cloud deployment strategies. This project bridges the gap between enterprise cloud services and open-source flexibility by deploying traditional open-source IoT tools on Azure VMs.

**Technologies:** Azure Virtual Machines, Terraform, Ansible, Docker, TimescaleDB, Mosquitto MQTT, Grafana, Python, MicroPython, Raspberry Pi Pico W

#### What I Built:
- Azure infrastructure automation using Terraform for VM provisioning and network security groups
- Multi-stage deployment pipeline with Bash scripts integrating Terraform and Ansible orchestration
- Dockerized IoT services including TimescaleDB for time-series data and Mosquitto MQTT broker
- Python data ingestion service that processes MQTT messages and stores to TimescaleDB
- Grafana dashboards with automated datasource provisioning for real-time monitoring
- Comprehensive deployment, monitoring, and teardown scripts with proper state management
- MicroPython firmware for Pico W with temperature and humidity sensors

**Links:**
- [IoT Backend Repo](https://github.com/nathandiez/iots6_a_oss)
- [IoT Sensor Repo](https://github.com/nathandiez/picosensor_net) 
- [Config Server](https://github.com/nathandiez/prox_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture3.md)
---

## Technical Skills
`Azure` `AWS` `GCP` `Docker` `Kubernetes` `Terraform` `Ansible` `Python` `C#` `GitHub Actions` `Git`

### Cloud Platforms
Azure, GCP, AWS, Linode

### Containers & Orchestration
Docker, Kubernetes, Helm

### Infrastructure as Code
Terraform, Ansible

### CI/CD & Version Control
GitHub Actions, Git

### Databases & Message Brokers
TimescaleDB, PostgreSQL, Mosquitto MQTT, Azure Data Lake

### Monitoring & Analytics
Grafana, Databricks

### Programming & Scripting
C#, Python, MicroPython, Bash

### Virtualization & Platforms
Proxmox, Azure Virtual Machines

---

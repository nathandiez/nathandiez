# Featured Projects

# 1 - Home IoT System - Azure Open-Source Stack
Live Grafana Dashboard: [View Dashboard](http://172.174.9.109:3000/d/7fee1038-fef5-4ef6-811e-15ce95b87ea8/home-iot-monitoring-system-dashboard) (Down for Maintenance) - Migrating to Kubernetes

Username: `iots6` | Password: `iots6`

Built and deployed on Azure using open-source technologies:
Azure, Terraform, Kubernetes, Ansible, Docker, TimescaleDB, Mosquitto MQTT, Grafana, Python
- [IoT Backend Repo](https://github.com/nathandiez/iots6_az_oss)
- [Config Server](https://github.com/nathandiez/az_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture3.md)
#### Description:
- Dual deployment options: Single VM with Docker containers or 3-node AKS cluster
- Infrastructure as Code: Terraform automation for Azure resources with integrated provisioning
- Automated deployment: Complete pipeline using Bash scripts with Terraform and Ansible orchestration
- Time series data processing: TimescaleDB for efficient sensor data storage and Mosquitto MQTT broker
- Real-time data pipeline: Python service processes MQTT messages and stores data with proper schema
- Monitoring and visualization: Grafana dashboards with external LoadBalancer access
- Enterprise features: Persistent storage, auto scaling, health checks, and comprehensive management tools

---

# 2 - Home IoT System - Proxmox Open-Source Stack
Built and deployed on Proxmox using open-source technologies:
Proxmox VMs, Terraform, Ansible, Docker, TimescaleDB, Mosquitto MQTT, Flask, Python
- [IoT Backend Repo](https://github.com/nathandiez/iots6_prox_oss)
- [Config Server](https://github.com/nathandiez/prox_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture2.md)
#### Description:
- Proxmox infrastructure automation using Terraform with local-exec for VM provisioning and network configuration
- Multi-stage deployment pipeline with Bash scripts integrating Terraform and Ansible orchestration
- Dockerized IoT services including TimescaleDB for time series data and Mosquitto MQTT broker
- Python data ingestion service that processes MQTT events and writes records to TimescaleDB
- Grafana dashboards for real-time visualization and monitoring
- Comprehensive deployment, testing, monitoring, and teardown scripts
  
---

# 3 - Home IoT System - AWS Open-Source Stack
Built and deployed on AWS using open-source technologies:
AWS, Terraform, Kubernetes, Ansible, Docker, TimescaleDB, Mosquitto MQTT, Grafana, Python
- [IoT Backend Repo](https://github.com/nathandiez/iots6_aws_oss)
- [Config Server](https://github.com/nathandiez/aws_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture5.md)
#### Description:
- Dual deployment options: Single VM with Docker containers or 3-node EKS cluster
- Infrastructure as Code: Terraform automation for AWS resources with integrated provisioning
- Automated deployment: Complete pipeline using Bash scripts with Terraform and Ansible orchestration
- Time series data processing: TimescaleDB for efficient sensor data storage and Mosquitto MQTT broker
- Real-time data pipeline: Python service processes MQTT messages and stores data with proper schema
- Monitoring and visualization: Grafana dashboards with external LoadBalancer access
- Enterprise features: Persistent storage, auto scaling, health checks, and comprehensive management tools

---

# 4 - Home IoT System - Azure Stack
Built and deployed on Azure using cloud native services:
Azure App Service, Terraform, Azure Data Lake, Databricks, C# .NET, Azure Key Vault
- [IoT Backend Repo](https://github.com/nathandiez/iots6_az_paas)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture.md)
#### Description:
- Azure infrastructure automation using Terraform for consistent cloud deployments
- RESTful API in C# .NET deployed to Azure App Service for real time data ingestion
- Automated data storage pipeline to Azure Data Lake with structured folder organization
- Databricks workspace integration for data analysis with custom Python notebooks
- Secure credential management using Azure Key Vault
- Comprehensive deployment and monitoring scripts

---

# 5 - Home IoT System - Azure Kubernetes Stack
Built and deployed on Azure using Kubernetes and cloud native technologies:
Azure Kubernetes Service (AKS), Terraform, Helm, Docker, TimescaleDB, Mosquitto MQTT, React, Flask, Python, cert manager, NGINX Ingress
- [IoT Backend Repo](https://github.com/nathandiez/iots2)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture4.md)
#### Description:
- Azure Kubernetes Service infrastructure automation using Terraform with custom VNet and subnet configuration
- Complete Helm chart deployment with comprehensive Kubernetes manifests for all system components
- Secure MQTT broker with TLS encryption using cert manager generated certificates and password authentication
- Python IoT service with Prometheus metrics collection for monitoring message processing and sensor data
- TimescaleDB hypertable implementation for efficient time series data storage with automated schema initialization
- React dashboard with Recharts visualization displaying real time temperature, humidity, pressure, motion and switch data
- Flask REST API with health checks and API key authentication for secure data access
- NGINX Ingress controller with dynamic IP configuration using nip.io DNS
- Comprehensive deployment automation with nuclear cleanup scripts and environment restoration capabilities
- Full CI/CD pipeline with GitHub Actions building and pushing multi architecture Docker images

---

# 6 - IoT Sensor Device Application - MicroPython
*Sensor code used across all IoT monitoring systems above*

Built with MicroPython for Raspberry Pi Pico W:
MicroPython, Raspberry Pi Pico W, WiFi, MQTT, I2C, OneWire, GPIO, SSD1306 OLED
- [IoT Device Repo](https://github.com/nathandiez/picosensor)
#### Description:
- Raspberry Pi Pico W firmware written in MicroPython that works across all my different backend infrastructures
- Reads multiple sensor types including BME280 environmental sensors, DS18B20 temperature probes, motion detectors, and switches
- Publishes sensor data via MQTT in JSON format to TimescaleDB backends running on Azure, AWS, Proxmox, and Kubernetes
- Built-in SSD1306 OLED display shows live sensor readings with custom font support for easy local monitoring
- Automatically downloads configuration updates from HTTP config servers for remote device management
- Dual-mode operation with development/production settings plus error recovery and automatic reboots
- Robust WiFi handling that reconnects automatically when network drops occur

---

## Technical Skills


Azure, GCP, AWS, Linode, Azure Kubernetes Service (AKS), Proxmox, Azure VMs, AWS EC2

Docker, Kubernetes, Helm, NGINX Ingress

Terraform, Ansible, GitHub Actions, Git

Python, C#, MicroPython, Bash, Flask, React, JavaScript

TimescaleDB, PostgreSQL, Mosquitto MQTT, Azure Data Lake

Grafana, Databricks, Prometheus, cert-manager, TLS/SSL

---

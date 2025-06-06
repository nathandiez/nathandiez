# Featured Projects

# 1 - Home IoT System - Azure Open-Source Stack
Built and deployed on Azure using open-source technologies:
Terraform with local-exec, Kubernetes (AKS), Ansible, Docker, TimescaleDB, Mosquitto MQTT, Grafana, Python
- [IoT Backend Repo](https://github.com/nathandiez/iots6_az_oss)
- [Config Server](https://github.com/nathandiez/az_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture3.md)

Live Grafana Dashboard: [View Dashboard](http://172.173.185.186:3000/d/7b1b05eb-0f28-4387-a0b8-46aafed5900b/home-iot-sensor-monitoring) (Down for Maintenance) - Migrating to Kubernetes.  
Username: `iots6` | Password: `iots6`

#### Description:
- Dual deployment options: Single VM with all Docker containers or 3-node AKS cluster
- Terraform and Ansible used to provision and configure all resources
- Use of local-exec to contain all build, deployment and verification automation within Terraform
- MQTT Pub/Sub architecture used to publish IoT events from Pico W devices to Python backend service
- IoT events written to TimescaleDB and visualized using Grafana
- Enterprise features: Persistent storage, auto scaling, health checks, and comprehensive testing/verification tools
---

# 2 - Home IoT System - AWS Open-Source Stack
Same tech stack as Azure project #1, but deployed to AWS. In progress: ArgoCD and Datadog
- [IoT Backend Repo](https://github.com/nathandiez/iots6_aws_oss)
- [Config Server](https://github.com/nathandiez/aws_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture5.md)
---

# 3 - Home IoT System - Proxmox Open-Source Stack
Same as Azure project 1 without kubernetes, but deployed only to local Proxmox Type-1 Hypervisor VM

- [IoT Backend Repo](https://github.com/nathandiez/iots6_prox_oss)
- [Config Server](https://github.com/nathandiez/prox_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture2.md)
---

# 4 - Home IoT System - Azure PaaS Stack
Azure App Service, Terraform, Azure Data Lake, Databricks, C# .NET, Azure Key Vault
- [IoT Backend Repo](https://github.com/nathandiez/iots6_az_paas)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture.md)
#### Description:
- RESTful API in C# .NET deployed to Azure App Service for real time data ingestion
- Automated data storage pipeline to Azure Data Lake with structured folder organization
- Databricks workspace integration for data analysis with custom Python notebooks
- Secure credential management using Azure Key Vault
---

# 5- IoT Sensor Device Application - MicroPython for Raspberry Pi Pico W

MicroPython, Raspberry Pi Pico W, MQTT, I2C, OneWire, GPIO, SSD1306 OLED
- [IoT Device Repo](https://github.com/nathandiez/picosensor)
#### Description:
- Firmware written in MicroPython that works across all backend above backend projects
- Reads multiple sensor types including temperature, humidity, barometric pressure, motion and switch states
- Publishes sensor data via MQTT in JSON format to IoT backend system.
- Support for on-board OLED display
---

## Technologies:

Azure, AWS, Linode, Azure Kubernetes Service (AKS), Amazon EKS, Proxmox, Azure VMs, AWS EC2, AWS VPC, AWS IAM

Docker, Kubernetes, Helm, NGINX Ingress, kubectl

Terraform, Ansible, GitHub Actions, Git

Python, C#, MicroPython, Bash, Flask, React, JavaScript

TimescaleDB, PostgreSQL, Mosquitto MQTT, Azure Data Lake, AWS EBS

Grafana, Databricks, Prometheus, cert-manager, TLS/SSL

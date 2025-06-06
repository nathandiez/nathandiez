# Featured Projects

# 1 - IoT System - Azure Open-Source Stack with Kubernetes
Built and deployed on Azure using open-source technologies:
Terraform with local-exec, Kubernetes (AKS), Ansible, Docker, TimescaleDB, Mosquitto MQTT, Grafana, Python
- [IoT Backend Repo](https://github.com/nathandiez/iots6_az_oss)
- [Config Server](https://github.com/nathandiez/az_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture3.md)

Live Grafana Dashboard: [View Dashboard](http://172.171.194.131:3000/d/b2d9b279-dce2-45dc-82ab-b86e8a56e420/home-iot-dashboard)
Username: `iots6` | Password: `iots6`

#### Description:
- Dual deployment options: Single VM with all Docker containers or 3-node AKS cluster
- Terraform and Ansible used to provision and configure all resources
- Use of local-exec to contain all build, deployment and verification automation within Terraform
- MQTT Pub/Sub architecture used to publish IoT events from Pico W devices to Python backend service
- IoT events written to TimescaleDB and visualized using Grafana
- Enterprise features: Persistent storage, auto scaling, health checks, and comprehensive testing/verification tools
---

# 2 - IoT System - AWS Open-Source Stack with Kubernetes
Same as Azure project 1, but with AWS, EKS and GitOps (ArgoCD & Helm)
- [IoT Backend Repo](https://github.com/nathandiez/iots6_aws_oss)
- [Config Server](https://github.com/nathandiez/aws_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture5.md)

What's Different:

- GitOps with ArgoCD ApplicationSets - push to Git and it deploys everywhere
- Helm charts for cleaner Kubernetes deployments
- Proper EBS storage setup
- Three separate environments with different configs and resource limits
---

# 3 - IoT System - Proxmox Open-Source Stack
Same as Azure project 1, but deployed only to local Proxmox Type-1 Hypervisor VM

- [IoT Backend Repo](https://github.com/nathandiez/iots6_prox_oss)
- [Config Server](https://github.com/nathandiez/prox_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture2.md)
---

# 4 - IoT System - Azure PaaS Stack
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

Azure, AWS, Linode, Proxmox

AKS, EKS, Azure VMs, EC2, VPC, IAM, EBS, Azure Data Lake

Docker, Kubernetes, Helm, kubectl

ArgoCD, GitHub Actions, NGINX Ingress

Terraform, Ansible, Git

Python, C#, MicroPython, Bash, JavaScript, Flask, React

TimescaleDB, PostgreSQL, Mosquitto MQTT

Grafana, Databricks, Prometheus, cert-manager, TLS/SSL

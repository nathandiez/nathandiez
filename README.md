# Featured Projects

# Home IoT Monitoring System - Azure Open-Source Stack
Live Grafana Dashboard: [View Dashboard]([http://74.235.232.127:3000/d/10711dc4-f67e-41ba-af3a-89801da2e582/iot-monitoring](http://172.174.9.109:3000/d/7fee1038-fef5-4ef6-811e-15ce95b87ea8/home-iot-monitoring-system-dashboard?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1))

Username: `iots6` | Password: `iots6`

Built and deployed on Azure using open-source technologies:
Azure VMs, Terraform, local-exec, Ansible, Docker, TimescaleDB, Mosquitto MQTT, Grafana, Python, MicroPython, Raspberry Pi Pico W
- [IoT Backend Repo](https://github.com/nathandiez/iots6_a_oss)
- [IoT Device Repo](https://github.com/nathandiez/picosensor_net) 
- [Config Server](https://github.com/nathandiez/prox_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture3.md)
#### Description:
- Azure infrastructure automation using Terraform, local-exec for VM provisioning and network security groups
- Multi stage deployment pipeline with Bash scripts integrating Terraform and Ansible orchestration
- Dockerized IoT services including TimescaleDB for time series data and Mosquitto MQTT broker
- Python data ingestion service that processes MQTT events and writes records to TimescaleDB
- Grafana dashboards for real time visualization
- Comprehensive deployment, testing, monitoring, and teardown scripts
- MicroPython app on Raspberry Pi Pico W devices measuring, temperature, humidity, barometric pressure, motion and switch state

---

# Home IoT Monitoring System - Proxmox Open-Source Stack
Built and deployed on Proxmox using open-source technologies:
Proxmox VMs, Terraform, Ansible, Docker, TimescaleDB, Mosquitto MQTT, Flask, Python, MicroPython, Raspberry Pi Pico W
- [IoT Backend Repo](https://github.com/nathandiez/iots6)
- [IoT Device Repo](https://github.com/nathandiez/picosensor_net) 
- [Config Server](https://github.com/nathandiez/prox_serveconfig)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture2.md)
#### Description:
- Same open-source stack as Azure project above.
  
---

# Home IoT Monitoring System - Azure Stack
Built and deployed on Azure using cloud native services:
Azure App Service, Terraform, Azure Data Lake, Databricks, C# .NET, MicroPython, Raspberry Pi Pico W, Azure Key Vault
- [IoT Backend Repo](https://github.com/nathandiez/iots6_net)
- [IoT Device Repo](https://github.com/nathandiez/picosensor_net)
- [Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture.md)
#### Description:
- Azure infrastructure automation using Terraform for consistent cloud deployments
- RESTful API in C# .NET deployed to Azure App Service for real time data ingestion
- Automated data storage pipeline to Azure Data Lake with structured folder organization
- Databricks workspace integration for data analysis with custom Python notebooks
- Secure credential management using Azure Key Vault
- Comprehensive deployment and monitoring scripts
- MicroPython app on Raspberry Pi Pico W devices measuring, temperature, humidity, barometric pressure, motion and switch state
  
---

# Home IoT Monitoring System - Azure Kubernetes Stack
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

## Technical Skills
`Azure` `AWS` `GCP` `Docker` `Kubernetes` `Terraform` `Ansible` `Python` `C#` `GitHub Actions` `Git`


Azure, GCP, AWS, Linode, Azure Kubernetes Service (AKS), Proxmox, Azure Virtual Machines

Docker, Kubernetes, Helm, NGINX Ingress

Terraform, Ansible, GitHub Actions, Git

Python, C#, MicroPython, Bash, Flask, React, JavaScript

TimescaleDB, PostgreSQL, Mosquitto MQTT, Azure Data Lake

Grafana, Databricks, Prometheus, cert-manager, TLS/SSL

---

# Featured Projects

# 1 - IoT System - AWS Open-Source Stack
Built and deployed on AWS using Terraform with Kubernetes (AKS 3-node cluster), Ansible, Docker, TimescaleDB, Mosquitto MQTT, Grafana, Python, ArgoCD and monitored with Datadog

[IoT Backend Repo](https://github.com/nathandiez/iots6_aws_oss)

[Config Server](https://github.com/nathandiez/aws_serveconfig)

[Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture5.md)
#### Description:
- Terraform and Ansible used to provision and configure all resources
- MQTT Pub/Sub architecture used to publish IoT events from Pico W devices to Python backend service
- IoT events written to TimescaleDB and visualized using Grafana
- GitOps with ArgoCD to deploy Helm charts to Kubernetes Cluster
- External Secrets Operator syncs with AWS Parameter Store keeps secrets out of Git
- Datadog monitoring cluster metrics, logs, and application performance
- Deployed to Dev, Staging and Prod environments with different configs and resource limits
- Local-exec option to deploy to single VM if desired for cost savings
---

# 2 - IoT System - Azure Open-Source Stack with Kubernetes
Same as AWS project 1 but with Azure and AKS

[IoT Backend Repo](https://github.com/nathandiez/iots6_az_oss)

[Config Server](https://github.com/nathandiez/az_serveconfig)

[Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture3.md)

---

# 3 - IoT System - Proxmox Open-Source Stack
Similar to AWS project 1, but deployed to a local Proxmox Type-1 Hypervisor VM.  No kubernetes, Grafana or Datadog.

[IoT Backend Repo](https://github.com/nathandiez/iots6_prox_oss)

[Config Server](https://github.com/nathandiez/prox_serveconfig)
 
[Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture2.md)

---

# 4 - IoT System - Azure PaaS Stack
Similar to AWS project 1 but leveraging Azure App Service, Data Lake, Databricks, C# .NET, Azure Key Vault

[IoT Backend Repo](https://github.com/nathandiez/iots6_az_paas)

[Architecture Diagram](https://github.com/nathandiez/nathandiez/blob/main/architecture.md)

#### Description:
- RESTful API in C# .NET deployed to Azure App Service for real time data ingestion
- IoT events written to Azure Data Lake with structured folder organization
- Databricks workspace integration for data analysis with custom Python notebooks
- Azure Key Vault for secure credential management
---

# 5- IoT Sensor Device App - MicroPython for Raspberry Pi Pico W

[IoT Device Repo](https://github.com/nathandiez/picosensor)
#### Description:
- Firmware written in MicroPython that works across all above backend projects
- Reads multiple sensor types including temperature, humidity, barometric pressure, motion and switch states
- Publishes sensor data via MQTT in JSON format to IoT backend system.
- Support for on-board OLED display

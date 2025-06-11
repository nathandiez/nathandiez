# IoT System Architecture - AWS

## Sensor Hardware
```mermaid
graph LR
  TEMP["Temperature Sensor"] --> PICO["Pico W<br/>MicroPython"]
  HUMID["Humidity Sensor"] --> PICO
  MOTION["Motion Sensor"] --> PICO
  SWITCH["Switch Sensor"] --> PICO
  PICO --> OLED["OLED Display"]
  PICO --> LED["Status LED"]
```

## Network & Data Flow
```mermaid
graph TB
  PICO["Pico W Sensors"] 
  CONFIG["Config Server<br/>Flask App"]
  
  PICO -->|"HTTP GET Config"| CONFIG
  PICO -->|"MQTT Publish"| MQTT_CLOUD["Cloud MQTT Broker"]
  
  classDef device fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
  classDef cloud fill:#0ea5e9,stroke:#0284c7,stroke-width:3px,color:#fff
  
  class PICO,CONFIG device
  class MQTT_CLOUD cloud
```

## VM Deployment
```mermaid
graph TB
  PICO_VM["Pico W"] 
  
  subgraph "AWS EC2"
    subgraph "Docker Services"
      MQTT["Mosquitto MQTT"]
      DB["TimescaleDB"]
      SERVICE["Python IoT Service"]
      GRAFANA["Grafana"]
    end
    DOCKER_NET["iot_network"]
  end
  
  PICO_VM -->|"MQTT Publish"| MQTT
  MQTT --> SERVICE
  SERVICE --> DB
  DB --> GRAFANA
  
  MQTT -.-> DOCKER_NET
  SERVICE -.-> DOCKER_NET
  DB -.-> DOCKER_NET
  GRAFANA -.-> DOCKER_NET
  
  classDef device fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
  classDef mqtt fill:#f59e0b,stroke:#d97706,stroke-width:3px,color:#fff
  classDef db fill:#3b82f6,stroke:#2563eb,stroke-width:3px,color:#fff
  classDef service fill:#8b5cf6,stroke:#7c3aed,stroke-width:3px,color:#fff
  classDef viz fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
  
  class PICO_VM device
  class MQTT mqtt
  class DB db
  class SERVICE service
  class GRAFANA viz
```

## Deployment Option 2: EKS Kubernetes
```mermaid
graph TB
  PICO_K8S["Pico W"]
  
  subgraph "AWS EKS Cluster"
    subgraph "Application Workloads"
      K8S_MQTT["Mosquitto MQTT<br/>LoadBalancer"]
      K8S_DB["TimescaleDB<br/>Persistent Storage"]
      K8S_SERVICE["IoT Service Pod"]
      K8S_GRAFANA["Grafana<br/>LoadBalancer"]
    end
    
    subgraph "Platform Services"
      ARGOCD["ArgoCD<br/>GitOps"]
      EXT_SEC["External Secrets<br/>Operator"]
      PARAM_STORE["AWS Parameter Store"]
      DATADOG["Datadog Agent<br/>Monitoring"]
    end
  end
  
  PICO_K8S -->|"MQTT Publish"| K8S_MQTT
  K8S_MQTT --> K8S_SERVICE
  K8S_SERVICE --> K8S_DB
  K8S_DB --> K8S_GRAFANA
  
  EXT_SEC <--> PARAM_STORE
  ARGOCD -.-> K8S_MQTT
  ARGOCD -.-> K8S_DB
  ARGOCD -.-> K8S_SERVICE
  ARGOCD -.-> K8S_GRAFANA
  DATADOG -.-> K8S_MQTT
  DATADOG -.-> K8S_DB
  DATADOG -.-> K8S_SERVICE
  
  classDef device fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
  classDef k8s fill:#326ce5,stroke:#1a5490,stroke-width:3px,color:#fff
  classDef aws fill:#ff9900,stroke:#cc7700,stroke-width:3px,color:#fff
  classDef gitops fill:#f97316,stroke:#ea580c,stroke-width:3px,color:#fff
  classDef monitor fill:#632ca6,stroke:#4c1d95,stroke-width:3px,color:#fff
  
  class PICO_K8S device
  class K8S_MQTT,K8S_DB,K8S_SERVICE,K8S_GRAFANA k8s
  class PARAM_STORE aws
  class ARGOCD,EXT_SEC gitops
  class DATADOG monitor
```

## Infrastructure as Code
```mermaid
graph LR
  subgraph "EC2 Deployment"
    TF_EC2["Terraform"]
    ANSIBLE["Ansible"]
  end
  
  subgraph "EKS Deployment"  
    TF_EKS["Terraform"]
    HELM["Helm Charts"]
  end
  
  TF_EC2 --> ANSIBLE
  TF_EKS --> HELM
  
  classDef iac fill:#6b7280,stroke:#4b5563,stroke-width:3px,color:#fff
  
  class TF_EC2,TF_EKS,ANSIBLE,HELM iac
```

## Data Schema & GitOps
```mermaid
graph TB
  PICO_DATA["Pico W"]
  MQTT_MSG["MQTT"]
  
  subgraph "GitOps Environments"
    DEV["Development<br/>iots6-dev"]
    STAGING["Staging<br/>iots6-staging"]
    PROD["Production<br/>iots6-prod"]
  end
  
  subgraph "TimescaleDB Schema"
    TABLE["sensor_data table<br/>Hypertable partitioned by time"]
    FIELDS["Fields:<br/>• device_id<br/>• temperature<br/>• humidity<br/>• pressure<br/>• motion<br/>• switch<br/>• timestamp"]
  end
  
  PICO_DATA --> MQTT_MSG
  MQTT_MSG --> DEV
  MQTT_MSG --> STAGING
  MQTT_MSG --> PROD
  DEV --> TABLE
  STAGING --> TABLE
  PROD --> TABLE
  TABLE --> FIELDS
  
  classDef device fill:#10b981,stroke:#059669,stroke-width:3px,color:#fff
  classDef data fill:#3b82f6,stroke:#2563eb,stroke-width:3px,color:#fff
  classDef env fill:#f59e0b,stroke:#d97706,stroke-width:3px,color:#fff
  
  class PICO_DATA device
  class MQTT_MSG,TABLE,FIELDS data
  class DEV,STAGING,PROD env
```

## Platform Services
```mermaid
graph LR
  subgraph "Secret Management"
    PARAM["AWS Parameter Store<br/>Encrypted Configuration"]
    EXT["External Secrets Operator<br/>Auto-sync"]
    K8S_SEC["Kubernetes Secrets<br/>Automatic Injection"]
  end
  
  subgraph "Monitoring & Observability"
    DD_AGENT["Datadog Agent<br/>Metrics & Logs"]
    DD_DASH["Datadog Dashboard<br/>Infrastructure Monitoring"]
    GRAFANA_MON["Grafana<br/>Application Metrics"]
  end
  
  PARAM --> EXT
  EXT --> K8S_SEC
  
  DD_AGENT --> DD_DASH
  DD_AGENT --> GRAFANA_MON
  
  classDef secret fill:#0078d4,stroke:#106ebe,stroke-width:3px,color:#fff
  classDef monitor fill:#632ca6,stroke:#4c1d95,stroke-width:3px,color:#fff
  
  class PARAM,EXT,K8S_SEC secret
  class DD_AGENT,DD_DASH,GRAFANA_MON monitor
```

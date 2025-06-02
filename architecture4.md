# IoT System Architecture
```mermaid
graph TB
  subgraph "Home Environment"
      subgraph "Physical Sensors"
          TEMP["Temperature Sensor<br/>I2C Digital"]
          HUMID["Humidity Sensor<br/>I2C Digital"]
          MOTION["Motion Sensor<br/>PIR Detection"]
          SWITCH["Switch Sensor<br/>Digital Input"]
      end
      
      subgraph "Raspberry Pi Pico W"
          PICO["Pico W Controller<br/>MicroPython Runtime"]
          OLED["OLED Display<br/>Real time Status"]
          LED["Status LED<br/>Health Indicators"]
      end
  end
  
  subgraph "Network Layer"
      WIFI["WiFi Network"]
      INTERNET["Internet<br/>(HTTP)"]
  end
  
  subgraph "Azure Infrastructure"
      subgraph "Azure Kubernetes Service (AKS)"
          subgraph "NGINX Ingress"
              INGRESS["NGINX Ingress Controller<br/>Load Balancer IP"]
          end
          
          subgraph "iot-system Namespace"
              subgraph "MQTT Services"
                  MQTT["Mosquitto MQTT<br/>TLS Enabled (8883)"]
                  MQTT_CERTS["TLS Certificates<br/>cert-manager"]
              end
              
              subgraph "Data Services"
                  TIMESCALE["TimescaleDB<br/>Hypertable Storage"]
                  IOT_SERVICE["Python IoT Service<br/>MQTT Subscriber"]
                  PROMETHEUS["Prometheus Metrics<br/>Port 8000"]
              end
              
              subgraph "Web Services"
                  BACKEND["Flask API<br/>REST Endpoints"]
                  FRONTEND["React Dashboard<br/>Recharts Visualization"]
              end
              
              subgraph "Test Services"
                  TEST_PUB["Test Publisher<br/>Simulated IoT Data"]
              end
          end
      end
      
      subgraph "Azure Resources"
          ACR["Azure Container Registry<br/>Docker Images"]
          VNET["Virtual Network<br/>10.0.0.0/16"]
          PUBLIC_IP["Public IP Address<br/>Static External IP"]
      end
  end
  
  subgraph "Automation & Management"
      TERRAFORM["Terraform<br/>AKS Provisioning"]
      HELM["Helm Charts<br/>K8s Deployment"]
      GITHUB["GitHub Actions<br/>CI/CD Pipeline"]
  end
  
  %% Data Flow Connections
  TEMP --> PICO
  HUMID --> PICO
  MOTION --> PICO
  SWITCH --> PICO
  PICO --> OLED
  PICO --> LED
  
  PICO ==>|"WiFi Connection"| WIFI
  WIFI ==> INTERNET
  
  INTERNET ==>|"MQTT/TLS:8883"| MQTT
  PICO ==>|"Publish Sensor Data"| MQTT
  TEST_PUB ==>|"Simulated Data"| MQTT
  
  MQTT ==> IOT_SERVICE
  IOT_SERVICE ==> TIMESCALE
  IOT_SERVICE ==> PROMETHEUS
  TIMESCALE -.->|"Query Data"| BACKEND
  
  INTERNET ==>|"HTTP via Ingress"| INGRESS
  INGRESS ==> FRONTEND
  INGRESS ==>|"/api routes"| BACKEND
  
  MQTT_CERTS -.-> MQTT
  
  GITHUB ==> ACR
  ACR -.-> IOT_SERVICE
  ACR -.-> BACKEND
  ACR -.-> FRONTEND
  ACR -.-> TEST_PUB
  
  TERRAFORM ==> VNET
  TERRAFORM ==> PUBLIC_IP
  TERRAFORM ==> ACR
  HELM ==> MQTT
  HELM ==> TIMESCALE
  HELM ==> IOT_SERVICE
  HELM ==> BACKEND
  HELM ==> FRONTEND
  
  PUBLIC_IP -.-> INGRESS
  
  %% Styling
  classDef device fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
  classDef sensor fill:#84cc16,stroke:#65a30d,stroke-width:2px,color:#fff
  classDef network fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#fff
  classDef storage fill:#3b82f6,stroke:#2563eb,stroke-width:2px,color:#fff
  classDef compute fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#fff
  classDef infrastructure fill:#6b7280,stroke:#4b5563,stroke-width:2px,color:#fff
  classDef container fill:#0ea5e9,stroke:#0284c7,stroke-width:2px,color:#fff
  classDef kubernetes fill:#326ce5,stroke:#1d4ed8,stroke-width:2px,color:#fff
  
  class PICO,OLED,LED device
  class TEMP,HUMID,MOTION,SWITCH sensor
  class WIFI,INTERNET network
  class TIMESCALE,ACR storage
  class IOT_SERVICE,BACKEND,FRONTEND,TEST_PUB compute
  class TERRAFORM,HELM,GITHUB infrastructure
  class MQTT,INGRESS,PROMETHEUS container
  class VNET,PUBLIC_IP,MQTT_CERTS kubernetes

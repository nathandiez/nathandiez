# IoT System Architecture
```mermaid
graph TB
   subgraph "Home Environment"
       subgraph "Physical Sensors"
           TEMP["Temperature Sensor<br/>I2C Digital"]
           HUMID["Humidity Sensor<br/>I2C Digital (if available)"]
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
   
   subgraph "Azure Cloud Platform"
       subgraph "Configuration"
           CONFIG["Blob Storage<br/>Device Config"]
           KEYVAULT["Key Vault<br/>Secure Secrets"]
       end
       
       subgraph "Data Ingestion"
           API_APP["Web App<br/>.NET 8.0 API"]
       end
       
       subgraph "Data Storage"
           DATA_LAKE["Data Lake<br/>ADLS Gen2"]
       end
       
       subgraph "Analytics"
           DATABRICKS["Databricks<br/>Spark Cluster"]
           NOTEBOOKS["Notebooks<br/>Python Analysis"]
       end
       
       subgraph "Security"
           MANAGED_ID["Managed Identity<br/>Service Authentication"]
       end
   end
   
   subgraph "Infrastructure"
       TERRAFORM["Terraform<br/>Infrastructure as Code"]
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
   
   INTERNET -.->|"Fetch Config"| CONFIG
   PICO ==>|"Publish Data"| API_APP
   
   API_APP --> MANAGED_ID
   API_APP ==> DATA_LAKE
   
   NOTEBOOKS ==> DATA_LAKE
   NOTEBOOKS --> DATABRICKS
   
   KEYVAULT -.-> API_APP
   KEYVAULT -.-> DATABRICKS
   TERRAFORM ==> CONFIG
   TERRAFORM ==> API_APP
   TERRAFORM ==> DATA_LAKE
   TERRAFORM ==> DATABRICKS
   
   %% Styling
   classDef device fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
   classDef sensor fill:#84cc16,stroke:#65a30d,stroke-width:2px,color:#fff
   classDef network fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#fff
   classDef storage fill:#3b82f6,stroke:#2563eb,stroke-width:2px,color:#fff
   classDef compute fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#fff
   classDef security fill:#ef4444,stroke:#dc2626,stroke-width:2px,color:#fff
   classDef infrastructure fill:#6b7280,stroke:#4b5563,stroke-width:2px,color:#fff
   
   class PICO,OLED,LED device
   class TEMP,HUMID,MOTION,SWITCH sensor
   class WIFI,INTERNET network
   class DATA_LAKE,CONFIG storage
   class API_APP,DATABRICKS,NOTEBOOKS compute
   class KEYVAULT,MANAGED_ID security
   class TERRAFORM infrastructure

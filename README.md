# IoT Project: Smart Traffic Monitoring System

## Overview
This project is a simulated IoT system designed to monitor urban traffic and environmental conditions. It integrates components such as sensors, middleware, databases, and dashboards to provide real-time insights, helping users observe traffic patterns and assess environmental impact.

## Features
- Simulates environmental metrics like traffic density, speed, CO2, PM2.5, PM10, and noise levels.
- Processes data using Telegraf for data collection and transformation.
- Stores time-series data in InfluxDB for long-term analysis.
- Visualizes data in Grafana with customizable dashboards.
- Fully containerized deployment using Docker Compose.

## Prerequisites
- Docker and Docker Compose installed on your system.

## Setup Instructions

### Step 1: Clone the Repository
```bash
git clone https://github.com/elsirleem/SE4IoT_project.git
cd SE4IoT_project
```

### Step 2: Start Docker Services
Run the following command to start all services (Traffic Simulator, InfluxDB, Telegraf, MQTT broker, and Grafana):
```bash
docker compose up --build
```

### Step 3: Access the Services
- **Grafana**: [http://localhost:3000](http://localhost:3000)
  - Default Username: `admin`
  - Default Password: `admin`
- **InfluxDB**: [http://localhost:8086](http://localhost:8086)
  - Default Username: `admin`
  - Default Password: `admin123`
- **Node-RED**: [http://localhost:1880](http://localhost:1880)

### Step 4: Stop Docker Services
To completely clean up when stopping (removes containers, local images, and volumes):
```bash
docker compose down --volumes --rmi local
```

## Project Structure
```
.
├── traffic_simulator/            # Traffic simulation service
│   ├── config.ini               # Simulation configuration
│   ├── Dockerfile              # Python simulation container setup
│   ├── requirements.txt        # Python dependencies
│   └── python_simulation.py    # Main simulation script
├── iot_project_nodered/        # Node-RED data directory
├── iot_project_mosquitto_config/ # Mosquitto MQTT broker config
├── mosquitto/                   # MQTT broker data directory
├── telegraf/                   # Telegraf service for data collection
└── grafana/                    # Grafana data directory
```

## Configuration
### Simulation Parameters (config.ini)
- MQTT broker settings
- Traffic and environmental thresholds
- Monitoring locations
- Publishing intervals

### Data Collection (telegraf.conf)
- MQTT subscription topics
- InfluxDB output settings
- Data processing rules

## Troubleshooting
- If the services don't start properly, check Docker logs:
  ```bash
  docker compose logs
  ```
- For specific service logs:
  ```bash
  docker compose logs [service_name]
  ```
  where [service_name] can be: traffic-simulator, telegraf, influxdb, mqtt-broker, or grafana

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

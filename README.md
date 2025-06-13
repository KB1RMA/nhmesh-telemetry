# nhmesh-telemetry

## Development

 - Install Python
 - Install Poetry

```
poetry install

poetry run nhmesh-telemetry/producer.py
poetry run nhmesh-telemetry/collector.py
```

## Docker Setup

 1. In the docker folder... copy the sample.env to telemetry.env and tweak values
 2. `docker compose up -d`

 ```
 docker compose logs
 ```

Kibana dashboard - https://localhost:5601

## Environment Variables

The following environment variables can be configured for the Docker containers:

### `nhmesh-telemetry/producer` Image Environment Variables

| Variable        | Default            | Description                                     |
| --------------- | ------------------ | ----------------------------------------------- |
| `LOG_LEVEL`     | `INFO`             | Logging level (DEBUG, INFO, WARNING, ERROR)     |
| `MQTT_ENDPOINT` | `mqtt.nhmesh.live` | MQTT broker address                             |
| `MQTT_PORT`     | `1883`             | MQTT broker port                                |
| `MQTT_USERNAME` | -                  | MQTT username for authentication                |
| `MQTT_PASSWORD` | -                  | MQTT password for authentication                |
| `NODE_IP`       | -                  | IP address of the Meshtastic node to connect to |
| `MQTT_TOPIC`    | `msh/US/NH/`       | Root MQTT topic for publishing messages         |

### `nhmesh-telemetry/collector` Image Environment Variables

| Variable                             | Default            | Description                                                 |
| ------------------------------------ | ------------------ | ----------------------------------------------------------- |
| `LOG_LEVEL`                          | `INFO`             | Logging level (DEBUG, INFO, WARNING, ERROR)                 |
| `MQTT_ENDPOINT`                      | `mqtt.nhmesh.live` | MQTT broker address                                         |
| `MQTT_PORT`                          | `1883`             | MQTT broker port                                            |
| `MQTT_USERNAME`                      | -                  | MQTT username for authentication                            |
| `MQTT_PASSWORD`                      | -                  | MQTT password for authentication                            |
| `MQTT_SUB_TOPIC`                     | `msh/US/#`         | MQTT topic pattern to subscribe to                          |
| `ES_ENDPOINT`                        | `large4cats`       | Elasticsearch endpoint URL                                  |
| `ES_USERNAME`                        | -                  | Elasticsearch username (typically `TELEMETRY_ES_USERNAME`)  |
| `ES_PASSWORD`                        | -                  | Elasticsearch password (typically `TELEMETRY_ES_PASSWORD`)  |
| `PACKET_PROCESSING_DELAY_SECONDS`    | `5.0`              | Seconds to delay packet processing to prioritize RF packets |
| `PACKET_PROCESSING_INTERVAL_SECONDS` | `0.5`              | Seconds interval for checking pending packets               |

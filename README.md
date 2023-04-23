# Prom-Grafana-Monitoring

## Prerequisites

|      Name      | Version  |
| :------------: | :------: |
|     Docker     | ^20.10.2 |
| Docker-compose | ^1.27.4  |

## Setup

### Run Node-exporter on target

```bash
docker run -d \
  --restart "unless-stopped" \
  --net="host" \
  --pid="host" \
  -v "/:/host:ro,rslave" \
  --name "node_exporter" \
  prom/node-exporter:latest \
  --path.rootfs=/host
```

### Configuartions

Modify [prometheus.yml](./config/prometheus.yml) and [rules.yml](./config/rules.yml)

## Run Prometheus

```bash
docker compose up -d; docker compose logs -f --tail=1000
```

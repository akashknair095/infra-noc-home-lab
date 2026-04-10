# Monitoring Stack

This directory contains configuration files and reference documentation for the Prometheus and Grafana monitoring stack, set up as part of the Linux-based NOC home lab.

## Overview

Prometheus scans and collects system health metrics from the NOC lab — including CPU, memory, storage, running processes, and network connectivity. Grafana takes that data and displays it on a web-based dashboard for easy monitoring.

## Components

| Component | Purpose | Port |
|---|---|---|
| Prometheus | Scrapes and stores metrics from all exporters | 9090 |
| Node Exporter | Collects OS-level metrics (CPU, memory, disk, network) and exposes them to Prometheus | 9100 |
| Nginx Exporter | Collects Nginx stats (active connections, request rate) and exposes them to Prometheus | 9113 |
| Grafana | Reads from Prometheus and displays metrics on a web dashboard | 3000 |

## Architecture

Exporters collect metrics from the system and Nginx, feed them into Prometheus for storage, and Grafana reads from Prometheus to display everything on a dashboard.

```
+----------------+     +---------------------+
|   Ubuntu VM    |---->| Node Exporter :9100 |---->+
+----------------+     +---------------------+     |
                                                    |  +-------------------+     +----------------+
+----------------+     +---------------------+     +-->| Prometheus  :9090 |---->| Grafana  :3000 |
|     Nginx      |---->| Nginx Exporter:9113 |---->+   +-------------------+     +----------------+
+----------------+     +---------------------+

```

## Directory Structure

```

monitoring/
├── prometheus/
│   └── prometheus.yml        # Scrape targets and intervals
├── exporters/
│   ├── node_exporter.service      # systemd unit for Node Exporter
│   ├── nginx_exporter.service     # systemd unit for Nginx Exporter
│   └── nginx_stub_status.conf     # Nginx stub_status location block
└── README.md

```

## Setup

See the full installation steps below. All components run as dedicated system users with no login shell.

### 1. Prometheus

```bash
sudo useradd --no-create-home --shell /bin/false prometheus
sudo mkdir /etc/prometheus /var/lib/prometheus
# Copy prometheus.yml from this repo to /etc/prometheus/prometheus.yml
sudo systemctl start prometheus
sudo systemctl enable prometheus
```

### 2. Node Exporter

```bash
sudo useradd --no-create-home --shell /bin/false node_exporter
sudo systemctl start node_exporter
sudo systemctl enable node_exporter
```

### 3. Nginx Exporter

Enable stub_status in Nginx first, then:

```bash
sudo systemctl start nginx_exporter
sudo systemctl enable nginx_exporter
```

### 4. Grafana

```bash
sudo apt-get install grafana -y
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

Access Grafana at `http://<vm-ip>:3000` — default credentials are `admin / admin`.

Add Prometheus as a data source with URL `http://localhost:9090`, then import dashboard ID **1860** (Node Exporter Full).

## Verification

Check all targets are up at `http://<vm-ip>:9090/targets` — all three jobs should show state **UP**.

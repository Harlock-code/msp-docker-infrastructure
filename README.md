# MSP / DevOps Lab — Docker Infrastructure

![banner](https://github.com/Harlock-code/Harlock-code/blob/main/banner_javi.png?raw=true)

![Docker](https://img.shields.io/badge/Docker-Infrastructure-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Proxmox](https://img.shields.io/badge/Proxmox-HomeLab-E57000?style=for-the-badge&logo=proxmox)
![Linux](https://img.shields.io/badge/Linux-Server-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Nginx Proxy Manager](https://img.shields.io/badge/Nginx_Proxy_Manager-Reverse_Proxy-009639?style=for-the-badge&logo=nginx)
![Technitium DNS](https://img.shields.io/badge/Technitium-DNS-2C89A0?style=for-the-badge)
![Self Hosted](https://img.shields.io/badge/Self_Hosted-Platform-1ABC9C?style=for-the-badge)

## 📌 Description

Base infrastructure repository for a self-hosted MSP/DevOps lab based on Docker, Linux, and Proxmox.

This repository contains the main stacks responsible for providing core services such as reverse proxy, internal DNS, centralized dashboard, basic monitoring, backups, and container administration.

It is part of a modular platform automated with Ansible, where each service can be deployed, configured, or removed declaratively.

---

# 🧱 Included Services

- Nginx Proxy Manager
- Technitium DNS
- Homepage
- Portainer
- Dozzle
- Uptime Kuma
- Duplicati
- Watchtower
- cAdvisor
- Node Exporter
- Prometheus / Grafana / Loki / Promtail

---

# ⚙️ Role Within the Platform

```text
msp-ansible-automation
        ↓
msp-docker-infrastructure
        ↓
Core Services
        ↓
DNS · Reverse Proxy · Dashboard · Monitoring · Backups
```

This repository represents the base infrastructure layer that supports the self-hosted applications of the MSP environment.

---

# 🚀 Main Features

- ✔ Reusable Docker Compose stacks
- ✔ Core services separated by folders
- ✔ Ready for automated deployment with Ansible
- ✔ Integration with external Docker networks
- ✔ Reverse Proxy using Nginx Proxy Manager
- ✔ Internal DNS using Technitium
- ✔ Centralized dashboard with Homepage
- ✔ Base for monitoring and backups
- ✔ Modular and extensible architecture

---

# 📂 Repository Structure

```text
nginx-proxy-manager/
technitium/
homepage/
portainer/
dozzle/
uptime-kuma/
duplicati/
watchtower/
monitoring/
cadvisor/
node-exporter/
```

Each folder contains its own `docker-compose.yml` and, when required, its own `.env.example` file.

---

# 🌐 Docker Networks

The infrastructure uses external Docker networks to separate services and simplify communication between stacks:

```text
proxy_net
monitoring_net
backend_net
```

Example:

```yaml
networks:
  proxy_net:
    external: true
```

---

# 🔁 Deployment Workflow

```text
Ansible
   ↓
Clones repositories
   ↓
Generates .env from .env.example
   ↓
Creates Docker networks
   ↓
Runs docker compose up -d
   ↓
Core services available
```

---

# 🔒 Reverse Proxy and DNS

The platform uses:

- **Nginx Proxy Manager** to publish internal services using friendly domain names.
- **Technitium DNS** to resolve internal laboratory domains.
- **Internal wildcard SSL** managed through Ansible automation.

Example:

```text
home.client.lab.local
vault.client.lab.local
nextcloud.client.lab.local
```

---

# 🖥️ Centralized Dashboard

Homepage acts as the central panel for visualizing deployed services.

It provides quick access to:

- Reverse Proxy
- Internal DNS
- Monitoring
- Backups
- Self-hosted applications
- Administration tools

---

# ⚙️ General Architecture Diagram

![architecture](https://github.com/Harlock-code/msp-docker-infrastructure/blob/main/screenshots/diagrama.png?raw=true)

---

# 🔗 Related Repositories

## Ansible Automation

https://github.com/Harlock-code/msp-ansible-automation

## Self-hosted Applications

https://github.com/Harlock-code/msp-docker-apps

---

# 🎯 Roadmap

- Improve the observability stack
- Integrate Grafana + Prometheus + Loki
- Add automated backups
- Prepare multi-client environments
- Integrate Terraform + Proxmox
- Add validations and healthchecks

---

# 📜 License

Project focused on learning, automation, and self-hosted infrastructure.

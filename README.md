# MSP / DevOps Lab — Docker Infrastructure

![banner](https://github.com/Harlock-code/Harlock-code/blob/main/banner_javi.png?raw=true)

![Docker](https://img.shields.io/badge/Docker-Infrastructure-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Proxmox](https://img.shields.io/badge/Proxmox-HomeLab-E57000?style=for-the-badge&logo=proxmox)
![Linux](https://img.shields.io/badge/Linux-Server-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Nginx Proxy Manager](https://img.shields.io/badge/Nginx_Proxy_Manager-Reverse_Proxy-009639?style=for-the-badge&logo=nginx)
![Technitium DNS](https://img.shields.io/badge/Technitium-DNS-2C89A0?style=for-the-badge)
![Self Hosted](https://img.shields.io/badge/Self_Hosted-Platform-1ABC9C?style=for-the-badge)

## 📌 Descripción

Repositorio de infraestructura base para un laboratorio MSP/DevOps self-hosted basado en Docker, Linux y Proxmox.

Este repositorio contiene los stacks principales encargados de proporcionar servicios core como reverse proxy, DNS interno, dashboard centralizado, monitorización básica y administración de contenedores.

Forma parte de una plataforma modular automatizada mediante Ansible, donde cada servicio puede desplegarse, configurarse o eliminarse de forma declarativa.

---

# 🧱 Servicios incluidos

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

# ⚙️ Rol dentro de la plataforma

```text
msp-ansible-automation
        ↓
msp-docker-infrastructure
        ↓
Core Services
        ↓
DNS · Reverse Proxy · Dashboard · Monitoring · Backups
```

Este repositorio representa la capa de infraestructura base sobre la que se apoyan las aplicaciones self-hosted del entorno MSP.

---

# 🚀 Características principales

- ✔ Stacks Docker Compose reutilizables
- ✔ Servicios core separados por carpetas
- ✔ Preparado para despliegue automático con Ansible
- ✔ Integración con redes Docker externas
- ✔ Reverse Proxy mediante Nginx Proxy Manager
- ✔ DNS interno mediante Technitium
- ✔ Dashboard centralizado con Homepage
- ✔ Base para monitorización y backups
- ✔ Arquitectura modular y extensible

---

# 📂 Estructura del repositorio

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

Cada carpeta contiene su propio `docker-compose.yml` y, cuando es necesario, su archivo `.env.example`.

---

# 🌐 Redes Docker

La infraestructura utiliza redes Docker externas para separar servicios y facilitar la comunicación entre stacks:

```text
proxy_net
monitoring_net
backend_net
```

Ejemplo:

```yaml
networks:
  proxy_net:
    external: true
```

---

# 🔁 Flujo de despliegue

```text
Ansible
   ↓
Copia repositorios
   ↓
Genera .env desde .env.example
   ↓
Crea redes Docker
   ↓
Ejecuta docker compose up -d
   ↓
Servicios core disponibles
```

---

# 🔒 Reverse Proxy y DNS

La plataforma utiliza:

- **Nginx Proxy Manager** para publicar servicios internos mediante dominios amigables.
- **Technitium DNS** para resolver dominios internos del laboratorio.
- **SSL wildcard interno** gestionado desde la automatización Ansible.

Ejemplo:

```text
home.cliente.lab.local
vault.cliente.lab.local
nextcloud.cliente.lab.local
```

---

# 🖥️ Dashboard centralizado

Homepage actúa como panel central para visualizar los servicios desplegados.

Permite acceder rápidamente a:
- Reverse Proxy
- DNS interno
- Monitorización
- Backups
- Aplicaciones self-hosted
- Herramientas de administración

---

# ⚙️ Diagrama Arquitectura General

![architecture](screenshots/infrastructure-diagram.png)

---

# 🔗 Repositorios relacionados

## Automatización Ansible

https://github.com/Harlock-code/msp-ansible-automation

## Aplicaciones self-hosted

https://github.com/Harlock-code/msp-docker-apps

---

# 🎯 Roadmap

- Mejorar stack de observabilidad
- Integrar Grafana + Prometheus + Loki
- Añadir backups automatizados
- Preparar entornos multi-cliente
- Integrar Terraform + Proxmox
- Añadir validaciones y healthchecks

---

# 📜 Licencia

Proyecto orientado a aprendizaje, automatización e infraestructura self-hosted.

# 🚀 Project 3 - Secure Cloud VM Deployment (Hybrid Monitoring)

This project focuses on deploying and securing a production-style Linux VM on **Google Cloud Compute Engine Free Tier**, then extending the existing local monitoring stack into a **hybrid cloud monitoring architecture**.

The idea behind this project was to move beyond local VirtualBox labs and start working with a real cloud VM while still keeping the same security-first and observability mindset from the previous projects.

The VM was deployed on **Google Compute Engine (e2-micro, Debian 12, us-central1)** and configured as a lightweight web server with **Nginx, UFW, Fail2Ban, and Node Exporter**.

On Day 2, the cloud VM was integrated into the existing on-premise monitoring stack from Project 2, allowing the local Prometheus server to scrape cloud metrics and send alerts to Telegram.

This project is intentionally built in phases:
- Day 1 → secure cloud VM deployment
- Day 2 → hybrid monitoring + cloud alerting
- Final phase → private hardening with Tailscale mesh networking

---

## 🎯 Project Goals
- Deploy a real cloud VM on Google Cloud Free Tier
- Apply Linux hardening and firewall rules
- Run a lightweight Nginx web service
- Extend local monitoring into hybrid cloud architecture
- Validate end-to-end alerting to Telegram
- Prepare the architecture for zero-trust hardening with Tailscale

---

## ☁️ Cloud Environment
- **Provider:** Google Cloud Platform
- **Service:** Compute Engine
- **Instance Type:** e2-micro (Free Tier eligible)
- **Region:** us-central1
- **OS:** Debian 12 (Bookworm)
- **Disk:** 10GB Standard Persistent Disk
- **Network Tier:** Standard
- **Web Service:** Nginx
- **Monitoring Agent:** Node Exporter

---

## 🔐 Day 1 - Secure Cloud VM Setup
The first phase focused on creating a clean and secure cloud VM baseline.

### Implemented
- Nginx web server deployment
- UFW enabled
- HTTP (80) allowed
- SSH (22) allowed for administration
- Fail2Ban enabled
- Basic landing page deployment
- System services configured with systemd
- Cost-safe Free Tier deployment choices

### Security Notes
At this stage, the VM was intentionally kept simple:
- only required ports exposed
- no unnecessary services installed
- minimal disk usage
- free-tier-safe network and disk choices

---

## 📊 Day 2 - Hybrid Cloud Monitoring
The second phase extended the existing local monitoring stack from Project 2 into a hybrid architecture.

The main objective here was to simulate a **real hybrid monitoring flow**, where an on-premise Prometheus server is able to scrape metrics from a cloud-hosted VM.

For this validation phase, Node Exporter on the GCP VM was temporarily exposed on port **9100** so the local Prometheus server could scrape metrics over the internet.

Once the target was confirmed UP, a dedicated Grafana dashboard was created to visualize the cloud VM health.

### Dashboard Panels
The dashboard currently includes:
- CPU Usage
- Memory Usage
- Disk Usage
- Network Receive
- Network Transmit
- System Load Average

This gives a clean NOC-style overview of the VM condition.

---

## 🚨 Cloud Alerting Validation
After the hybrid scrape path was stable, the next step was validating the full alert lifecycle.

The existing **Prometheus + Alertmanager + Flask Telegram webhook** pipeline from Project 2 was reused.

To test the flow, CPU stress was intentionally generated on the cloud VM.

### Validation Result
The following alert lifecycle was successfully confirmed:
- FIRING alert
- Telegram notification received
- CPU recovered
- RESOLVED alert received

This was important because it validated not only anomaly detection, but also alert recovery visibility.

This now completes the full observability path:

```text
GCP VM → Node Exporter → Local Prometheus → Alertmanager → Telegram Webhook → Telegram Bot
```

---

## 🖼️ Key Screenshots
### 📈 Hybrid Grafana Dashboard
`screenshots/day-2/grafana-hybrid-cloud-dashboard.png`

### 🚨 Telegram Cloud Alert
`screenshots/day-2/telegram-cloud-alert-fired-resolved.png`

---

## 🧭 Architecture Evolution
This project is designed as an architecture journey.

### Current State
Temporary public scrape path:
```text
Local Prometheus → Public IP:9100 → GCP VM
```

### Final Planned State
Private zero-trust mesh:
```text
Local Prometheus → Tailscale Private IP → GCP VM
```

This final phase will remove public metric exposure and improve operational flexibility when switching between different internet connections.

---

## 🧠 Key Lessons Learned
A few important practical lessons from this phase:
- Free Tier cost visibility still shows raw cost before savings
- Ephemeral public IPs create operational overhead
- Public metric scraping works, but is not ideal long term
- Hybrid monitoring is a strong stepping stone before private mesh networking
- Alert validation should always include FIRING and RESOLVED states

---

## 🔜 Next Improvement
The final improvement planned for this project is:

### 🌐 Tailscale Private Mesh Hardening
Goals:
- remove public 9100 exposure
- stable private connectivity from anywhere
- no dependency on changing public IPs
- zero-trust style observability path
- cleaner long-term hybrid architecture

This will be the final hardening phase before the project is fully production-ready.

---

## 🏆 Portfolio Outcome
This project demonstrates:
- real cloud VM deployment
- Linux hardening
- firewall design
- hybrid observability
- Grafana dashboarding
- alert lifecycle validation
- cloud cost awareness
- architecture evolution planning

This is the bridge between local infrastructure labs and real cloud operations.
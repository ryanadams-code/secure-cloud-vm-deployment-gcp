## Day 1 Milestone - Secure Cloud VM Deployment
### Completed
- Real GCP Compute Engine VM deployment
- Debian 12 Bookworm on e2-micro
- Public nginx landing page
- UFW firewall hardening
- fail2ban brute-force protection
- Strict budget control under free-tier constraints

### Public Access
The landing page is reachable via the VM public IP and validates successful 
internet-facing deployment.

### Security Highlights- Layered firewall controls- Minimal exposed ports- fail2ban active- dedicated admin sudo usergit

**Architecture Decision: Centralized Monitoring (Hub & Spoke)**

- **Hub (Control Plane):** Admin Lab Server (VirtualBox, 192.168.57.103).
  - Runs: Prometheus, Grafana, Alertmanager.
  - Reason: Stable local network, sufficient RAM (4GB+), zero latency for dashboards.
- **Spoke (Workload):** Google Cloud Compute Engine (Public Cloud).
  - Runs: Nginx (App) + Node Exporter (Metrics Endpoint).
  - Reason: Demonstrates ability to securely expose telemetry data over the public internet to a centralized collector.

This design avoids redundant resource consumption on the low-tier `e2-micro` instance and mirrors real-world enterprise monitoring topologies.
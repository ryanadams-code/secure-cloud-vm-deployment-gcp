# Architecture Overview

## Objective
Build a secure public cloud VM on Google Cloud that exposes a web service 
while maintaining layered host and network security.

## Infrastructure Components

- Google Cloud Compute Engine
- Debian GNU/Linux 12 (Bookworm) x86_64- e2-micro instance
- 10 GB standard persistent disk- Standard network tier
- Ephemeral external IPv4- Nginx web server- UFW host firewall
- fail2ban brute-force protection
## High-Level Flow
Internet
    │
    1
    ▼
GCP VPC Firewall
    │
    ▼
Compute Engine VM
    ├── Nginx :80
    ├── SSH :22
    ├── UFW
    └── fail2ban

Security Layers:

Layer 1 — Cloud Firewall
Used GCP VPC firewall rules to allow HTTP traffic and keep SSH reachable.

Layer 2 — Host Firewall
UFW only allows: - 22/tcp - 80/tcp

Layer 3 — Intrusion Prevention
fail2ban is enabled to reduce brute-force SSH attempts. 
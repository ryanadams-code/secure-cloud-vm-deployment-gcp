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

### Security Highlights- Layered firewall controls- Minimal exposed ports- fail2ban active- dedicated admin sudo user
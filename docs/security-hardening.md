# Security Hardening

## SSH Access
A dedicated administrative user was created for operational access.

### Admin User
    - username: `ryanadmin`
    - added to sudo group
This separates administrative actions from the default login workflow.

## UFW Host Firewall
Installed and enabled UFW.

### Allowed Ports
    - 22/tcp → SSH
    - 80/tcp → Nginx

### Default Security Outcome
All other ports are denied by default.
This ensures the VM only exposes the minimum required services.

## fail2ban
Installed fail2ban and enabled it as a systemd service.

### Protection Scope
    - monitors authentication logs
    - blocks repeated failed login attempts
    - protects SSH from brute-force attacks

## Defense in Depth
Security is applied in multiple layers:
    1. GCP VPC firewall
    2. UFW host firewall
    3. fail2ban intrusion prevention

This layered design improves resilience against common internet-facing threats.
# Day 1 - Secure Cloud VM Setup

Day 1 focused on creating a clean and secure baseline VM on Google Cloud Compute Engine.

The main objective was to deploy a lightweight Linux web server that is:
- Free Tier safe
- easy to monitor
- hardened enough for public HTTP exposure
- simple enough to extend later

## What Was Implemented
- Debian 12 VM on e2-micro
- Nginx installation
- custom landing page
- UFW enabled
- Fail2Ban enabled
- HTTP access allowed
- SSH administration access
- Node Exporter prepared for Day 2

## Why This Matters
This phase established the secure foundation for everything that followed.

Instead of jumping straight into monitoring, the focus was first placed on:
- OS stability
- firewall visibility
- service management
- cost-safe cloud decisions

This made Day 2 hybrid monitoring much cleaner to implement.
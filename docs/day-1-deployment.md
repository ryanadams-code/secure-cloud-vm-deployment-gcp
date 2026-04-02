#  Day 1 - Initial Cloud VM Deployment

## Goal
Deploy a secure Debian VM on Google Cloud under strict free-tier budget limits.

## What I Did
    - Created a dedicated GCP project for Project 3
    - Linked the Google Cloud trial billing account
    - Enabled Compute Engine API- Deployed 1 VM using `e2-micro`
    - Selected region `us-central1-a`
    - Chose Debian 12 Bookworm x86_64
    - Used 10 GB standard persistent disk- Switched network tier to Standard
    - Used ephemeral public IPv4
    - Enabled HTTP firewall access

## Post-Deployment Setup
After the VM was running, I:
    - updated and upgraded system packages
    - installed nginx
    - verified nginx service was active
    - deployed a custom landing page
    - fixed UTF-8 encoding issue for emoji rendering
    - created a dedicated admin sudo user
    - enabled UFW
    - enabled fail2ban

## Validation Results
Confirmed the following:
    - VM status = running
    - nginx = active (running)
    - landing page accessible from public IP
    - UFW active
    - fail2ban active
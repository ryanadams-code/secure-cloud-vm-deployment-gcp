#Troubleshooting Notes

## Billing Link Issue
### Problem
Compute Engine API could not be enabled initially.

### Root Cause
The default tutorial project was not linked to the active trial billing account.

### Fix
Created a dedicated project and linked billing manually.

## Architecture Mismatch
### Problem
Ubuntu image initially failed with architecture mismatch.

### Root Cause
Machine type selection was previously mismatched with image architecture.

### Fix
Selected `E2 e2-micro` and used Debian 12 Bookworm x86_64.

## Unexpected Monthly Estimate
### Problem
The VM creation page showed approximately $6/month.

### Root Cause
The UI displayed retail list price before free-tier discounts.

### Fix
Validated free-tier eligible specs:
    - e2-micro
    - us-central1
    - standard disk
    - ephemeral IP

## UTF-8 Emoji Issue
### Problem
Rocket emoji rendered as broken characters on the landing page.

### Root Cause
HTML page did not explicitly define UTF-8 charset.

### Fix
Added:
<meta charset="UTF-8">

## Browser SSH Stability
### Problem
Package upgrade felt slow and browser SSH connection stability was uncertain.
### Fix
Allowed the upgrade to complete server-side and avoided interrupting the browser session.
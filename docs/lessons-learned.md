# Lessons Learned

This project ended up being a really useful bridge between local infrastructure labs and actual cloud operations.

A few practical lessons stood out during the build:

## 1. Free Tier Still Shows Raw Cost
Even under free tier, GCP still shows raw usage cost before applying savings.

This was useful for learning how billing visibility works in real cloud environments.

## 2. Public IP Dependency Adds Operational Friction
Stopping and starting the VM can change the public IP, which means monitoring targets may need updates.

This highlighted why stable private overlay networking is valuable.

## 3. Hybrid Monitoring Is a Great Intermediate Step
Before jumping straight into zero-trust private networking, validating the scrape path over the internet helped prove the observability flow first.

## 4. Alert Validation Should Include Recovery
Seeing both FIRING and RESOLVED states gave much better confidence than only testing the trigger condition.

This mirrors real incident lifecycle visibility.
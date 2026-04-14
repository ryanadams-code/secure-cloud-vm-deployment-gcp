# Day 2 - Cloud Alerting Validation

Once the scrape path was stable, the next step was validating whether alerts from the cloud VM could travel through the full existing alert pipeline.

The existing stack from Project 2 was reused:
- Prometheus
- Alertmanager
- Flask Telegram webhook
- Telegram bot

## Test Method
CPU spikes were intentionally generated on the GCP VM using stress testing.

This was done to validate:
- threshold detection
- firing state
- Telegram delivery
- resolved state

## Validation Result
The full alert lifecycle was confirmed successfully:
- FIRING notification received
- RESOLVED notification received

This was an important milestone because it proved the hybrid monitoring path was no longer dashboard-only, but fully operational from an incident-response perspective.
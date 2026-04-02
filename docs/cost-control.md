# Cost Control Strategy

## Budget Controls
Because this project uses limited cloud credits, cost control was part of the 
deployment design.

### Billing Safety
- Trial credit: USD $5
- Budget alert: USD $1
- Thresholds:- 25%- 50%- 75%- 90%- 100%

## Free-Tier Design Choices
To remain within free-tier limits, the VM was designed with:
    - e2-micro- us-central1 region
    - 10 GB standard persistent disk
    - standard network tier
    - ephemeral public IP
    - no snapshots
    - no extra disks
    - no Ops Agent

## Operational Discipline
Best practice workflow:
- stop VM when not in use
- avoid unnecessary uptime
- avoid additional billable services
- delete resources after project completion

## Key Learning
The VM creation page showed retail monthly pricing before free-tier savings were applied.
This was an important lesson in understanding GCP billing UI behavior.
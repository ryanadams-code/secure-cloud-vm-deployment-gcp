# Lessons Learned - Day 1

The biggest lesson from Day 1 was understanding that Google Cloud's VM 
estimate page shows the retail list price before free-tier savings are 
applied.

At first this created confusion because the VM was already aligned with free
tier eligible specifications.

Another important lesson was checking hidden defaults such as snapshot 
schedules and premium settings, since these can silently increase cost.

I also learned the importance of validating CPU architecture compatibility 
early. The ARM vs x86 mismatch could have been avoided by confirming the 
machine family first.

From the web deployment side, the UTF-8 issue reminded me that infrastructure 
work also overlaps with application-level debugging.

The strongest technical takeaway today was the value of defense in depth:
    - cloud firewall
    - host firewall
    - fail2ban
    
This project now feels closer to a real production deployment than a simple 
VM lab.
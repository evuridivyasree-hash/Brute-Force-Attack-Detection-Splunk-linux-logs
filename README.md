#  Brute Force Attack Detection using Splunk

## Project Overview

This project focuses on detecting brute force attacks by analyzing Linux authentication logs using Splunk.

## Tools Used

* Splunk Enterprise
* Linux Authentication Logs (`auth.log`)

## Use Case

Detect multiple failed login attempts from the same IP address indicating a brute force attack.

## Implementation Steps

1. Ingested `auth.log` into Splunk
2. Filtered failed login attempts
3. Extracted IP addresses using SPL (`rex`)
4. Counted attempts per IP
5. Applied threshold (`count > 5`)
6. Built dashboards for visualization
7. Configured alerts using cron scheduling

## SPL Query Used

```
index=main sourcetype=linux_secure "Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| where count > 5
```

## Alert Configuration

* Type: Scheduled
* Interval: Every 5 minutes
* Trigger: Number of results > 0
* Action: Add to Triggered Alerts

## Results

* Detected multiple attacker IPs
* Visualized attack patterns
* Successfully triggered alerts

## Key Learnings

* Handling duplicate and noisy log data
* Importance of time-based filtering
* Real-world SOC alerting workflow
  
## Screenshots

![brute force attack linux auth log1 png](https://github.com/user-attachments/assets/01d1e21a-05d4-4820-a2b5-8c8f80b0d60d)
![brute force attack linux auth log2 png](https://github.com/user-attachments/assets/bd5fae63-2292-425e-81c3-0ebd21c4fafd)
![brute force attack linux auth log3 png](https://github.com/user-attachments/assets/96e8fd4d-8955-4407-a1f0-deeacbf50400)
![brute force attack linux auth log4 png](https://github.com/user-attachments/assets/2255b81c-addd-4b61-9558-bbf250574a32)
![brute force attack linux auth log5 png](https://github.com/user-attachments/assets/0911211c-77d7-4e63-b99f-9b5daae045fe)
![brute force attack linux auth log6 png](https://github.com/user-attachments/assets/9ed052dc-a479-4abf-aaab-3b33cc0cb058)
![brute force attack linux auth log7 png](https://github.com/user-attachments/assets/57bf62a9-136b-4c7d-864a-f62865477a22)
![brute force attack linux auth log8 png](https://github.com/user-attachments/assets/dcfe8253-0f05-4d3e-bf42-0140d6138e4f)
![brute force attack linux auth log9 png](https://github.com/user-attachments/assets/00128f24-657f-4475-8bb2-eccb452337a8)
![brute force attack linux auth log10 png](https://github.com/user-attachments/assets/a1f04e9c-e653-4e32-afc8-a134c657deac)

## Conclusion

This project demonstrates how SIEM tools like Splunk can be used to detect and monitor brute force attacks in real time.


 Open to SOC Analyst / Cybersecurity roles# Brute-Force-Attack-Detection-Splunk-linux-logs

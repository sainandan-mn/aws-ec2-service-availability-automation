# AWS EC2 Apache Auto-Healing Automation

## Overview

This project implements a lightweight automation to maintain service availability on an AWS EC2 instance.
It ensures that a critical Linux service is automatically restarted if it becomes unavailable.

Apache HTTP Server is used as a representative service, but the approach applies to any systemd-managed service.

## Problem
In real environments, services can stop due to instance reboots, configuration changes, memory pressure, or accidental human actions.
Relying on manual recovery increases downtime and operational risk.

## Solution
A Bash script periodically checks the service state using systemctl.
If the service is found inactive, it is restarted automatically and the recovery event is logged.

The script is executed on a schedule using cron, allowing the system to recover without human intervention.

## Execution Flow
Cron (scheduled run)
→ Monitoring script executes
→ systemctl checks service state
→ Service restarted if inactive
→ Recovery event logged

## Technology Stack
- AWS EC2
- Ubuntu Linux
- Bash
- Cron
- systemctl
- Apache HTTP Server (example service)

## Validation
The service was manually stopped to simulate a failure.
The automation detected the downtime, restarted the service, and recorded the event with a timestamp.

## Notes
This project focuses on basic service-level recovery for a single instance.
It is not a replacement for full monitoring or alerting systems, but demonstrates core availability and automation concepts.
=======

This project demonstrates a simple but realistic infrastructure automation use case on AWS EC2.

An Apache HTTP Server is deployed on an Ubuntu EC2 instance and monitored using a Bash script. A cron job periodically checks the service status and automatically restarts Apache if it stops, ensuring ba$

The goal of this project is to understand Linux service management, automation, and failure recovery in a cloud environment.

---

## Use Case

In real-world environments, services may stop due to:

* Instance reboots
* Configuration changes
* Resource issues   
* Accidental manual stops
   
If recovery depends on manual action, it increases downtime and operational risk.
This project implements a lightweight auto-healing mechanism to reduce such downtime.

---

## High-Level Flow
   
```
User Browser
   ↓
AWS EC2 (Ubuntu 24.04)   
   ↓
Apache HTTP Server (Port 80)
   ↓
systemd service management
   ↓
Cron job (every 5 minutes)
   ↓
Bash monitoring script
   ↓
Apache restarted if inactive
   ↓
Recovery event logged
```

---

## Project Structure

```
aws-ec2-apache-auto-healing/
├── README.md              # Project documentation
├── scripts/
│   └── check_service.sh   # Bash auto-healing script
├── cron.txt               # Cron job configuration
└── screenshots/           # Proof of execution
```

---

## Components Explained

### 1. Apache HTTP Server

* Runs on an Ubuntu 24.04 EC2 instance
* Serves a simple web page on port 80
* Used as a representative Linux service

---

### 2. Auto-Healing Script (`scripts/check_service.sh`)

The Bash script:

* Checks Apache service status using `systemctl`
* Restarts the service if it is not active
* Logs recovery events with timestamps

This approach can be reused for any systemd-managed service.

---

### 3. Cron Job (`cron.txt`)

* Runs the monitoring script every 5 minutes
* Enables continuous, unattended health checks
* Ensures recovery even if the service stops unexpectedly
   
---

## Validation and Testing

The auto-healing behavior was verified by:

1. Manually stopping the Apache service
2. Allowing the cron job to execute the script
3. Confirming Apache was restarted automatically
4. Verifying recovery entries in the log file

Screenshots in the `screenshots/` folder show:

* Apache service status
* Website availability
* Cron configuration
* Auto-healing log output

These serve as proof of end-to-end execution.

---
   
## Key Learnings

* Linux service management using `systemctl`
* Bash scripting for automation
* Cron scheduling
* AWS EC2 fundamentals
* Basic infrastructure reliability concepts
* Failure detection and recovery workflows


---

## Author

Sai Nandan
Aspiring Cloud / DevOps Engineer

---





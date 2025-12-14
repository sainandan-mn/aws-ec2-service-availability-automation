# EC2 Service Availability Automation

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


# Enterprise IT Incident Response Runbooks

## Overview

This document provides operational troubleshooting procedures for common enterprise infrastructure and application incidents.

The scenarios are based on practical infrastructure monitoring and troubleshooting experience.

All examples are anonymized. The procedures are reference workflows and require adaptation and validation before use in production.

## 1. Branch WAN Connectivity Failure

### Symptoms

- Primary or backup WAN link reported as unavailable
- Increased ICMP packet loss
- High network latency
- Branch users reporting connectivity problems

### Investigation

1. Identify the affected branch and WAN provider.
2. Check the latest Zabbix availability data.
3. Verify ICMP connectivity from the assigned Zabbix proxy.
4. Compare primary and backup link status.
5. Review router interfaces and routing information.
6. Check VPN or tunnel connectivity where applicable.
7. Verify whether the issue affects one link or both.

### Recovery

- Escalate provider-side failures to the relevant ISP.
- Restore connectivity through the approved backup path when supported.
- Verify connectivity to required corporate services.
- Confirm that monitoring data and alerts return to normal.

### Escalation

Both WAN links unavailable: Disaster severity.

## 2. Jira / Tomcat Service Unavailable

### Symptoms

- Jira web interface inaccessible
- HTTP monitoring check fails
- Tomcat process or service is stopped
- High application response time

### Investigation

1. Verify server network reachability.
2. Check HTTP/HTTPS endpoint availability.
3. Review Tomcat service status.
4. Inspect server CPU and memory usage.
5. Check available disk space.
6. Review Tomcat and Jira application logs.
7. Examine database connectivity when indicated by logs.

### Recovery

- Restore a stopped service only after checking the cause and following the approved change procedure.
- Resolve resource or dependency problems.
- Verify Jira login and essential application functionality.
- Confirm monitoring recovery.

### Escalation

Escalate to application or database administrators when troubleshooting identifies application-level or database-related failures.

## 3. SharePoint Portal Unavailable

### Symptoms

- SharePoint portal inaccessible
- HTTP availability checks fail
- Users report login errors
- Portal response times increase

### Investigation

1. Check server reachability.
2. Verify HTTP/HTTPS availability.
3. Review IIS application pools and related services.
4. Check Windows event logs.
5. Review CPU, memory, and disk utilization.
6. Check relevant authentication and SQL Server dependencies.
7. Determine whether the issue affects one service or multiple components.

### Recovery

- Apply corrective actions according to the identified cause.
- Coordinate application pool or service restarts through approved procedures.
- Verify authentication and portal functionality.
- Confirm monitoring status returns to normal.

### Escalation

Escalate to SharePoint, Windows, or SQL Server specialists depending on the affected component.

## 4. Nextcloud Service Degradation

### Symptoms

- Nextcloud unavailable or slow
- Login failures
- Background job delays
- Database or Redis errors

### Investigation

1. Verify HTTP/HTTPS endpoint availability.
2. Check server CPU, memory, and disk utilization.
3. Review web server and PHP service health.
4. Examine Nextcloud application logs.
5. Check database availability.
6. Verify Redis service health.
7. Review scheduled background jobs.
8. Investigate AD/LDAP authentication when login failures occur.

### Recovery

- Address confirmed infrastructure or service failures.
- Restore dependent services using approved procedures.
- Verify user login and file access.
- Confirm that background processing and monitoring recover.

## 5. Zabbix Proxy Communication Failure

### Symptoms

- Monitoring data becomes stale
- Proxy communication errors
- Multiple hosts stop reporting metrics

### Investigation

1. Check proxy host availability.
2. Verify the Zabbix proxy service status.
3. Review proxy logs.
4. Check network connectivity to the central Zabbix server.
5. Inspect firewall permissions.
6. Verify proxy hostname and server configuration.
7. Check the proxy database and local resource utilization.

### Recovery

- Resolve connectivity or configuration problems.
- Restart services only when justified.
- Verify that proxy communication resumes.
- Confirm new monitoring data arrives.

## 6. Incident Documentation

Each incident record should contain:

| Field | Description |
|---|---|
| Incident ID | Unique tracking identifier |
| Start time | When the issue was detected |
| Affected service | Application, server, or network |
| Severity | Business and operational impact |
| Symptoms | Observed errors and alerts |
| Investigation | Checks performed and evidence collected |
| Root cause | Confirmed cause, if identified |
| Corrective action | Steps taken to restore service |
| Recovery time | Confirmed restoration timestamp |
| Follow-up | Preventive actions and improvements |

## 7. Post-Incident Review

After service restoration:

1. Establish the incident timeline.
2. Review alerts, logs, and relevant metrics.
3. Document the confirmed root cause or remaining uncertainty.
4. Identify opportunities to improve detection.
5. Review preventive actions and responsible teams.
6. Update monitoring rules and runbooks when necessary.

## Validation Status

These runbooks are documentation examples, not evidence of completed lab tests.

Future lab work will include controlled incident simulations, troubleshooting evidence, and sanitized screenshots.

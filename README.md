
# Enterprise Infrastructure & Service Monitoring

### Zabbix | Netdata | Network Monitoring | IT Operations

## Overview

This repository documents enterprise infrastructure and service monitoring practices based on hands-on experience supporting a distributed IT environment with 1,000+ users across 31 branches.

The project focuses on infrastructure visibility, proactive alerting, service availability, and efficient incident troubleshooting using Zabbix and Netdata.

All examples are anonymized and adapted for demonstration purposes. No internal company configurations, credentials, or sensitive network information are included.

## Key Monitoring Areas

### 1. Network & WAN Monitoring
- Primary and backup WAN link availability
- ICMP reachability, packet loss, and response time
- Branch connectivity monitoring
- Link failure detection and alerting

### 2. Server & Infrastructure Monitoring
- CPU, memory, and disk utilization
- Windows and Linux server availability
- Network interface traffic
- Infrastructure health dashboards

### 3. Application & Service Monitoring
- HTTP/HTTPS service availability
- Response time monitoring
- Windows service and process monitoring
- Monitoring of enterprise applications such as Jira, SharePoint, and Nextcloud

### 4. Alerting & Incident Response
- Zabbix triggers and event severity
- Alert notification workflows
- Incident identification and troubleshooting
- Proactive monitoring practices

## Technologies

- **Monitoring:** Zabbix, Netdata
- **Operating Systems:** Windows Server, Debian Linux
- **Networking:** TCP/IP, ICMP, LAN/WAN, VPN
- **Infrastructure Automation:** Ansible
- **Applications:** Jira, SharePoint, Nextcloud

## Technical Case Studies

The following case studies document enterprise monitoring and infrastructure operations scenarios.

| Case Study | Focus |
|---|---|
| [Branch WAN Monitoring](docs/branch-wan-monitoring.md) | Primary/backup WAN connectivity, ICMP, triggers |
| [Jira & Tomcat Monitoring](docs/jira-tomcat-monitoring.md) | Application availability, services, performance |
| [SharePoint Portal Monitoring](docs/sharepoint-portal-monitoring.md) | IIS, web availability, SQL dependencies |
| [Nextcloud Service Monitoring](docs/nextcloud-service-monitoring.md) | Web services, Redis, cron, database health |
| [Monitoring Architecture](docs/architecture.md) | Zabbix Server, proxies, monitoring design |

See the [Project Index](docs/monitoring-project-index.md) for documentation and implementation status.

> Implementation details are anonymized. Configuration examples require validation in an isolated lab environment.

## Zabbix Configuration Examples

The repository includes a sample Zabbix 7.4 template for monitoring primary and backup WAN connections.

- [Dual WAN Monitoring Template](template_wan_dual_link_zabbix74.yaml)

The template includes:
- Primary and backup WAN ICMP availability
- Packet loss and latency monitoring
- Primary WAN failure detection
- Backup WAN failure detection
- Simultaneous WAN failure alerting

**Validation status:** The template has not yet been imported or tested in a dedicated lab.

## Project Roadmap

### Documentation

- [x] Document monitoring architecture
- [x] Document branch WAN monitoring scenarios
- [x] Add initial Zabbix template example
- [x] Document Jira/Tomcat monitoring
- [x] Document SharePoint portal monitoring
- [x] Document Nextcloud monitoring

### Next Steps

- [ ] Document Zabbix Proxy deployment and configuration
- [ ] Document monitoring dashboards
- [ ] Add incident response and troubleshooting runbooks
- [ ] Add additional Zabbix templates
- [ ] Document alerting and escalation workflows

### Lab Validation

- [ ] Set up a dedicated Zabbix lab environment
- [ ] Test template import and configuration
- [ ] Validate monitoring items and triggers
- [ ] Test WAN failure scenarios
- [ ] Add sanitized screenshots and test results

## About

This portfolio project showcases practical experience in IT infrastructure operations, enterprise monitoring, network troubleshooting, and infrastructure reliability.

The repository will continue to expand with reproducible lab examples, technical documentation, and operational runbooks.

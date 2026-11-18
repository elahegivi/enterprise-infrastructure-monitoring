
# Enterprise Monitoring — Technical Project Index

## Overview

This portfolio documents enterprise infrastructure monitoring, service operations, and incident troubleshooting across a multi-site environment supporting 1,000+ users and 31 branches.

The case studies cover network monitoring, distributed monitoring architecture, business-critical applications, operational dashboards, and incident response.

All technical examples are anonymized. Lab validation is planned separately.

## Architecture & Monitoring Infrastructure

| Project | Technical Scope |
|---|---|
| [Monitoring Architecture](architecture.md) | Zabbix Server, distributed proxies, Netdata, network segmentation |
| [Zabbix Proxy Deployment](zabbix-proxy-deployment.md) | Active proxies, Debian 12, Office/DMZ, connectivity troubleshooting |
| [Monitoring Dashboards & Alerting](monitoring-dashboards-alerting.md) | Operational dashboards, alert severity, monitoring metrics |

## Network Monitoring

| Project | Technical Scope |
|---|---|
| [Branch WAN Monitoring](branch-wan-monitoring.md) | Primary/backup WAN links, ICMP checks, packet loss, latency, disaster alerts |

## Enterprise Application Monitoring

| Project | Technical Scope |
|---|---|
| [Jira & Tomcat Monitoring](jira-tomcat-monitoring.md) | Application availability, Tomcat services, performance metrics, HTTPS |
| [SharePoint Portal Monitoring](sharepoint-portal-monitoring.md) | IIS, web availability, authentication, SQL Server dependencies |
| [Nextcloud Monitoring](nextcloud-service-monitoring.md) | Web availability, Redis, cron jobs, database and LDAP dependencies |

## IT Operations & Incident Management

| Project | Technical Scope |
|---|---|
| [Incident Response Runbooks](incident-response-runbooks.md) | WAN outages, Jira, SharePoint, Nextcloud, Zabbix Proxy troubleshooting |

## Configuration Examples

- [Zabbix 7.4 Dual WAN Template](../template_wan_dual_link_zabbix74.yaml)

This YAML file is an example configuration awaiting import and functional validation in a dedicated lab.

## Implementation & Validation

The repository documents practical engineering experience alongside proposed improvements.

The following work remains planned:

- Reproduce the monitoring environment in a lab
- Import and validate Zabbix templates
- Simulate infrastructure and application incidents
- Verify trigger behavior and alert workflows
- Add anonymized screenshots and test evidence
- Expand reusable configuration examples

## Security & Confidentiality

No real infrastructure addresses, production credentials, internal hostnames, or confidential company configurations are intentionally published.

Examples must be reviewed before publication to ensure sensitive details are removed.

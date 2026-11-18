
# Branch WAN Monitoring with Zabbix

## 1. Objective

Monitor primary and backup WAN connections across enterprise branches using Zabbix.

The solution aims to:
- Detect connectivity failures
- Monitor packet loss and network latency
- Distinguish primary and backup link failures
- Raise a critical alert when both links are unavailable
- Improve incident response and troubleshooting

This example uses fictional IP addresses and branch names.

## 2. Example Environment

Branch: Branch-01

| Connection | Provider | Monitoring IP |
|---|---|---|
| Primary WAN | Provider-A | 192.0.2.10 |
| Backup WAN | Provider-B | 198.51.100.10 |

The addresses above are reserved for documentation.

Monitoring is performed from a Zabbix proxy with network access to both targets.

## 3. Host Macros

Define the following macros at host level:

| Macro | Example Value |
|---|---|
| {$PRIMARY_LINK_IP} | 192.0.2.10 |
| {$BACKUP_LINK_IP} | 198.51.100.10 |
| {$PRIMARY_PROVIDER} | Provider-A |
| {$BACKUP_PROVIDER} | Provider-B |

Host-level macros make the monitoring template reusable across branches.

## 4. Zabbix Items

Create the following simple-check items.

### Primary WAN Availability

Name: Primary WAN - ICMP Availability

Key:
`icmpping[{$PRIMARY_LINK_IP}]`

Type: Simple check

Type of information: Numeric (unsigned)

Update interval: 1m

### Backup WAN Availability

Name: Backup WAN - ICMP Availability

Key:
`icmpping[{$BACKUP_LINK_IP}]`

Type: Simple check

Type of information: Numeric (unsigned)

Update interval: 1m

### Primary WAN Packet Loss

Key:
`icmppingloss[{$PRIMARY_LINK_IP}]`

Units: %

### Backup WAN Packet Loss

Key:
`icmppingloss[{$BACKUP_LINK_IP}]`

Units: %

### Primary WAN Response Time

Key:
`icmppingsec[{$PRIMARY_LINK_IP}]`

Units: s

### Backup WAN Response Time

Key:
`icmppingsec[{$BACKUP_LINK_IP}]`

Units: s

## 5. Trigger Design

Example template name:

`Template WAN Dual Link`

### Trigger 1: Primary WAN Down

Severity: High

Expression:

`max(/Template WAN Dual Link/icmpping[{$PRIMARY_LINK_IP}],#3)=0`

This trigger fires after three consecutive unsuccessful ICMP checks.

### Trigger 2: Backup WAN Down

Severity: Warning

Expression:

`max(/Template WAN Dual Link/icmpping[{$BACKUP_LINK_IP}],#3)=0`

### Trigger 3: Both WAN Links Down

Severity: Disaster

Expression:

`max(/Template WAN Dual Link/icmpping[{$PRIMARY_LINK_IP}],#3)=0 and max(/Template WAN Dual Link/icmpping[{$BACKUP_LINK_IP}],#3)=0`

This trigger identifies simultaneous loss of both monitored WAN paths.

Configure trigger dependencies or event correlation to avoid duplicate notifications during a complete branch outage.

## 6. Monitoring Dashboard

Recommended dashboard widgets:

- Branch connectivity status
- Primary WAN availability
- Backup WAN availability
- ICMP packet loss
- ICMP response time
- Active WAN alerts
- Recent connectivity incidents

## 7. Incident Response Workflow

1. Receive a WAN availability alert.
2. Verify connectivity from the monitoring proxy.
3. Check whether the issue affects the primary, backup, or both connections.
4. Investigate the router, network interface, VPN, and ISP connection.
5. Escalate to the relevant network or service provider team.
6. Confirm recovery and document the incident.

## 8. Operational Considerations

- ICMP reachability alone does not prove that all business applications are operational.
- Monitoring targets must be reachable from the assigned Zabbix proxy.
- ICMP collection requires the Zabbix server or proxy to have the appropriate fping configuration.
- Separate monitoring of VPN tunnels and application availability may be necessary.
- Trigger thresholds should be validated against real network conditions.
- Provider information is maintained through host macros.

## 9. Future Improvements

- Add WAN availability trend reports
- Implement prolonged outage notifications
- Introduce trigger dependency rules
- Add automated incident documentation
- Export a reusable Zabbix monitoring template
- Add lab-tested screenshots and configuration examples

# Jira / Tomcat — Application Monitoring Case Study

**Category:** Application observability · Windows Server · Zabbix  
**Status:** Documented from hands-on monitoring work; public examples remain untested in the lab.

## Scenario

Monitor a business-critical Jira application hosted on Windows Server, using the Jira Windows service and a Tomcat-based application runtime. The monitoring design separates connectivity, web availability, application runtime, operating-system resource use, and database availability to make incidents easier to diagnose.

> This is an anonymized portfolio case study. It contains no actual server names, internal addresses, credentials, or client data.

## Monitoring coverage

| Layer | Monitored signals | Implementation status |
|---|---|---|
| Network | ICMP availability, loss and response time | Implemented |
| Web | HTTPS availability, HTTP status and response time via Zabbix web scenario | Implemented |
| Application | Jira Windows service state (`service.info["jira",state]`) | Implemented |
| Tomcat | Process presence, CPU and private memory | Implemented |
| Certificates | TLS certificate expiration | Implemented |
| Database | MySQL availability | Present in monitoring scope |
| Virtualization | ESXi/vCenter layer | Deferred during migration |
| Logs / JMX | Detailed log parsing and JMX metrics | Out of scope in the referenced phase |

## Example Zabbix item and trigger

A Windows service state check can use:

```text
service.info["jira",state]
```

In a Zabbix lab, verify the actual service name and state mappings before applying a condition. An example alert for a non-running service is:

```text
last(/JIRA/service.info["jira",state])<>0
```

`JIRA` is a **sample host name**; replace it with the lab host. The condition is intentionally broad and should be reviewed against the service's possible states and the team's escalation policy.

## Example operational alert scenarios

- Jira Windows service stops responding.
- The Tomcat process disappears or consumes unusually high CPU/memory.
- The HTTPS check fails or web response time exceeds a reviewed threshold.
- TLS certificate expiration approaches its renewal threshold.
- Database availability fails independently of application response.

Observed operational configuration work included response-time alerting, Tomcat CPU and memory thresholds, SSL expiration alerts and Jira service alerts. Thresholds are not universal recommendations; they require a lab baseline.

## Incident triage — illustrative runbook

1. Check Zabbix event time and whether the failure is network-wide or Jira-specific.
2. Confirm HTTPS availability and recent response-time trend.
3. Check Windows service state and Tomcat process metrics.
4. Review host CPU, memory, disk and network conditions.
5. Check the database availability signal.
6. Correlate findings and escalate to the relevant application/database team.
7. Confirm service recovery, close the event and record the root cause.

## Evidence to add after lab testing

- [ ] Zabbix item and trigger screenshots from a synthetic test host
- [ ] Web scenario screenshot using a public or local test endpoint
- [ ] Anonymized alert-to-recovery sequence
- [ ] Baseline and threshold rationale
- [ ] Exportable template validated with Zabbix 7.4

## Notes on results

No outage reduction, MTTR improvement, or performance percentage is claimed here because no verified before/after measurement has been provided.

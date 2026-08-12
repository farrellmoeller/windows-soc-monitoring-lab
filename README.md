# Windows SOC Monitoring Lab

Hands-on Windows security monitoring and SOC investigation lab demonstrating endpoint logging, authentication analysis, process monitoring, Sysmon telemetry, DNS analysis, and event correlation in an isolated virtual environment.

## Project Overview

This project documents the configuration and investigation of a Windows 11 endpoint designed to simulate a basic Security Operations Center (SOC) monitoring workflow.

Native Windows Advanced Audit Policy and Sysmon were used to collect security-relevant endpoint telemetry. Controlled activity was then generated and analyzed through Windows Event Viewer to validate the logging configuration and practice reconstructing endpoint activity.

The project focuses on the defensive side of cybersecurity: establishing visibility, identifying relevant events, analyzing event context, correlating multiple telemetry sources, and documenting findings.

> **Environment:** All activity documented in this repository was performed in an isolated personal lab environment for educational and portfolio purposes.

---

## Objectives

The lab was designed to demonstrate the ability to:

- Configure security-relevant Windows auditing
- Validate endpoint logging coverage
- Analyze successful and failed authentication activity
- Investigate process creation and command-line execution
- Monitor PowerShell activity
- Use Sysmon for enhanced endpoint telemetry
- Analyze DNS activity associated with endpoint processes
- Correlate authentication and process events
- Reconstruct activity using timestamps and event context
- Document findings in a structured SOC investigation report

---

## Lab Environment

| Component | Purpose |
|-----------|---------|
| Windows 11 | Monitored endpoint |
| VMware Workstation | Virtualized lab environment |
| Windows Event Viewer | Event review and investigation |
| Windows Security Log | Native authentication and process telemetry |
| Windows Advanced Audit Policy | Security auditing configuration |
| Sysmon | Enhanced process and DNS telemetry |
| PowerShell | Controlled administrative activity and analysis |

**Endpoint hostname:** `SOC-WIN11-01`

A clean baseline snapshot was created before additional monitoring configuration and controlled testing.

---

## Telemetry Analyzed

### Windows Security Events

| Event ID | Description | Investigation Use |
|----------|-------------|-------------------|
| 4624 | Successful Logon | Identify successful authentication activity |
| 4625 | Failed Logon | Investigate unsuccessful authentication attempts |
| 4688 | Process Creation | Analyze process and command-line execution |

### Sysmon Events

| Event ID | Description | Investigation Use |
|----------|-------------|-------------------|
| 1 | Process Create | Enhanced process, parent process, command-line, user, and hash context |
| 22 | DNS Query | Associate DNS activity with endpoint processes |

---

## Investigation Workflow

The project follows a basic endpoint investigation workflow:

**Lab Baseline → Logging Configuration → Activity Generation → Event Collection → Event Analysis → Correlation → Findings**

### 1. Establish the Endpoint Baseline

A Windows 11 virtual machine was configured as the monitored endpoint and a clean baseline snapshot was preserved.

### 2. Configure Security Auditing

Windows Advanced Audit Policy was configured to provide visibility into security-relevant activity including authentication, process creation, account management, policy changes, privilege use, and system activity.

### 3. Validate Authentication Telemetry

Successful and failed authentication activity was generated and analyzed using Windows Security Event IDs 4624 and 4625.

### 4. Analyze Process Execution

Windows Event ID 4688 was used to examine process creation and command-line activity, including controlled PowerShell execution.

### 5. Analyze Enhanced Sysmon Telemetry

Sysmon Event ID 1 provided additional process context, while Event ID 22 demonstrated DNS query visibility from endpoint processes.

### 6. Correlate Events

A custom Windows Event Viewer view consolidated authentication and process events to support chronological analysis and endpoint triage.

### 7. Document Findings

The resulting telemetry was analyzed and summarized in a structured SOC investigation report.

---

## Evidence

Evidence is organized by investigation stage so that each area can be reviewed independently.

| Section | Description |
|---------|-------------|
| [Lab Setup](evidence/lab-setup/) | Windows 11 VM configuration, endpoint networking, update status, and baseline snapshot |
| [Logging Configuration](evidence/logging-configuration/) | Windows Advanced Audit Policy configuration and verification |
| [Authentication Analysis](evidence/authentication-analysis/) | Successful and failed Windows authentication events |
| [Process Analysis](evidence/process-analysis/) | Windows 4688 and Sysmon Event ID 1 process telemetry |
| [DNS Analysis](evidence/dns-analysis/) | Sysmon Event ID 22 DNS query telemetry |
| [Event Correlation](evidence/event-correlation/) | Custom Event Viewer workflow for correlating authentication and process activity |

Each evidence directory contains screenshots and accompanying analysis explaining the investigative value of the observed telemetry.

---

## Key Findings

### Authentication Auditing Operational

Windows Security auditing successfully captured both successful and failed authentication activity, providing account, logon, timestamp, and failure context useful for endpoint investigation.

### Process and Command-Line Visibility Operational

Event ID 4688 provided visibility into executed processes and command-line activity, allowing controlled endpoint actions to be reconstructed from Windows Security telemetry.

### Sysmon Enhanced Endpoint Visibility

Sysmon supplemented native Windows auditing with additional process context and DNS query telemetry.

### PowerShell Activity Observable Across Multiple Sources

Controlled PowerShell activity was observable through both Windows Security auditing and Sysmon, demonstrating the value of using complementary telemetry sources during an investigation.

### Event Correlation Improved Investigative Context

Combining authentication and process events into a custom Event Viewer view provided a more efficient method for reviewing event sequences and reconstructing endpoint activity.

---

## DNS Validation Note

Sysmon Event ID 22 DNS telemetry was successfully observed during the lab.

A controlled `nslookup` process was also captured through Windows process creation auditing. However, a corresponding Sysmon Event ID 22 for that specific controlled lookup was not conclusively identified.

This distinction is intentionally retained so the project reflects only telemetry that was directly validated during testing.

---

## Investigation Report

The complete investigation, including objectives, telemetry analysis, findings, and conclusions, is documented here:

**[View the SOC Investigation Report](investigation/README.md)**

---

## Repository Structure

```text
windows-soc-monitoring-lab/
│
├── README.md
│
├── evidence/
│   ├── lab-setup/
│   ├── logging-configuration/
│   ├── authentication-analysis/
│   ├── process-analysis/
│   ├── dns-analysis/
│   └── event-correlation/
│
└── investigation/
    └── README.md
```

---

## Skills Demonstrated

- Windows security monitoring
- Windows Event Viewer analysis
- Windows Advanced Audit Policy
- Windows Security Event analysis
- Sysmon telemetry analysis
- Authentication monitoring
- Process and command-line analysis
- PowerShell monitoring
- DNS telemetry analysis
- Event correlation
- Timeline reconstruction
- Endpoint triage
- SOC investigation methodology
- Technical documentation

---

## Project Takeaways

This project demonstrates how endpoint telemetry from native Windows auditing and Sysmon can be combined to support a structured security investigation.

Rather than treating individual events as isolated indicators, the lab emphasizes examining user activity, process execution, command-line context, DNS telemetry, and event chronology together.

The resulting environment provides a foundation for future work involving centralized log collection, SIEM ingestion, detection engineering, alert development, threat hunting, and more advanced incident-response exercises.

---

## Scope and Ethics

All activity documented in this repository was performed on systems owned and controlled within an isolated personal lab environment.

The project is intended solely for cybersecurity education, defensive security practice, and professional portfolio development.

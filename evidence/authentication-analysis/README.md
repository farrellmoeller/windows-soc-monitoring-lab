# Authentication Analysis Evidence

This directory contains evidence demonstrating the monitoring and analysis of Windows authentication activity within the SOC lab.

Windows Security auditing was configured to capture both successful and failed authentication attempts. Controlled authentication activity was then generated and reviewed through Windows Event Viewer to validate that the endpoint produced usable security telemetry.

Key Windows Security events analyzed include:

- **Event ID 4624 — Successful Logon**
  - Used to identify successful authentication activity.
  - Reviewed account, domain, logon type, and timestamp information.

- **Event ID 4625 — Failed Logon**
  - Used to identify unsuccessful authentication attempts.
  - Reviewed the targeted account, logon type, failure reason, status codes, and originating workstation information.

These events demonstrate how authentication telemetry can be used by a SOC analyst to identify normal logon activity and investigate potentially suspicious authentication failures.

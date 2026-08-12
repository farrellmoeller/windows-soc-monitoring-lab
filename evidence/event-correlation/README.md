# Event Correlation Evidence

This directory contains evidence demonstrating event correlation and investigation techniques using Windows Security telemetry.

After validating individual authentication and process creation events, a custom Event Viewer view was created to consolidate security-relevant activity into a single investigative workspace.

The custom view includes:

- **Event ID 4624 — Successful Logon**
- **Event ID 4625 — Failed Logon**
- **Event ID 4688 — Process Creation**

Combining these event types allows an analyst to review authentication and process activity together, establish timelines, and identify relationships between user logons and subsequent endpoint activity.

During the lab, controlled activity was generated and reviewed through the custom view to demonstrate how multiple security events can be correlated during an investigation.

This approach reduces the need to search individual Windows logs separately and provides a more efficient starting point for endpoint triage and incident analysis.

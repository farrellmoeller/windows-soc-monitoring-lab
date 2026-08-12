# Process Analysis Evidence

This directory contains evidence demonstrating process monitoring and command-line analysis using native Windows Security auditing and Sysmon.

Process creation auditing was enabled on the Windows 11 endpoint to provide visibility into programs and commands executed by users. Command-line process auditing was also enabled to provide additional context for Event ID 4688.

Sysmon supplemented native Windows telemetry by recording detailed process creation events, including process relationships, command-line information, user context, and cryptographic hashes.

Key telemetry analyzed includes:

- **Windows Security Event ID 4688 — Process Creation**
  - Identifies newly created processes.
  - Provides process name, creator process, user context, and command-line information.
  - Used to examine controlled execution of utilities and PowerShell commands.

- **Sysmon Event ID 1 — Process Create**
  - Provides enhanced process creation telemetry.
  - Records process and parent process information.
  - Captures command-line arguments, user context, and process hashes.

Controlled administrative commands were executed during the lab and correlated with the resulting Windows Security and Sysmon events. This demonstrates how a SOC analyst can use process telemetry to reconstruct endpoint activity and identify potentially suspicious command execution.

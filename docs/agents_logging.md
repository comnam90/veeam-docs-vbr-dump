---
title: "Exporting Logs from Veeam Agent Computers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_logging.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Exporting Logs from Veeam Agent Computers


If Veeam Agent computer is connected to a Veeam backup server as a member of a protection group for pre-installed Veeam Agents, you can export Veeam Agent logs directly from the Veeam Agent computer.

When you export product logs, Veeam Agent collects its log files, exports them to an archive file in the tar.gz format and saves this archive file to the following folder on the Veeam backup server:

for Veeam Backup & Replication on Linux

|  |
| --- |
| /var/log/VeeamBackup/Endpoint/Other/AgentLogs/<computer\_name> |

for Veeam Backup & Replication on Microsoft Windows

|  |
| --- |
| C:\ProgramData\Veeam\Backup\Endpoint\Other\AgentLogs\<computer\_name> |

where <computer\_name> — name of the computer with Veeam Agent installed.

For more information on exporting product logs from a Veeam Agent computer, see the following user guides depending on the Veeam Agent that you use:

* [Veeam Agent for Microsoft Windows](https://helpcenter.veeam.com/docs/agentforwindows/configurator/exportdebuglogs.html?ver=13)
* [Veeam Agent for Linux](https://helpcenter.veeam.com/docs/agentforlinux/userguide/installation_operation_mode_logs.html?ver=13)
* [Veeam Agent for Mac](https://helpcenter.veeam.com/docs/agentformac/userguide/installation_operation_mode_logs.html?ver=13)
* [Veeam Agent for Oracle Solaris](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/installation_operation_mode_logs.html?ver=13)
* [Veeam Agent for IBM AIX](https://helpcenter.veeam.com/docs/agentforaix/userguide/installation_operation_mode_logs.html?ver=13)



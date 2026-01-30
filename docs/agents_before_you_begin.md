---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_before_you_begin.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Before you start using the Veeam Agent management functionality in Veeam Backup & Replication, consider the following:

* If you have already been using Veeam Agents with Veeam Backup & Replication in the standalone mode, after you start managing this Veeam Agent with Veeam Backup & Replication, Veeam Agent will start a new backup chain on a target location. You cannot continue the existing backup chain that was created by Veeam Agent operating in the standalone mode.
* You cannot map a Veeam Agent backup job or backup policy configured in Veeam Backup & Replication to a Veeam Agent backup chain created by a standalone Veeam Agent on a backup repository.

Related Topics

* [Prerequisites and Limitations for Protection Groups](agents_protection_group_before.md)
* [Prerequisites and Limitations for Veeam Agent Backup Jobs (Windows Computers)](agent_job_before.md)
* [Prerequisites and Limitations for Veeam Agent Backup Jobs (Linux Computers)](agent_job_before_linux.md)
* [Prerequisites and Limitations for Veeam Agent Backup Policies (Windows Computers)](agent_policy_win_before.md)
* [Prerequisites and Limitations for Veeam Agent Backup Policies (Linux Computers)](agent_policy_before_linux.md)
* [Prerequisites and Limitations for Veeam Agent Backup Policies (Unix Computers)](agent_policy_before_unix.md)
* [Prerequisites and Limitations for Veeam Agent Backup Policies (Mac Computers)](agent_policy_before_mac.md)



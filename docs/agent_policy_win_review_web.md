---
title: "Step 13. Review Backup Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_win_review_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 13. Review Backup Job Settings


At the Summary step of the wizard, complete the backup policy configuration process.

1. Review the settings of the configured Veeam Agent backup policy in the Backup job settings section. To copy the settings to the clipboard, click Copy to Clipboard.
2. Click Finish to close the wizard.

|  |
| --- |
| TIP |
| You can use the [Get-VBRComputerBackupJob](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputerbackupjob.html?ver=13) and [Start-VBRComputerBackupJob](https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcomputerbackupjob.html?ver=13) cmdlets to manage the backup policy from the PowerShell command line. The cmdlet with the current policy's name is also displayed under PowerShell cmdlet for starting the backup job. |

Keep in mind that Veeam Backup & Replication does not immediately apply backup policy to computers included in protection groups for pre-installed Veeam Agents. Veeam Agents installed on computers that are included in these groups connect to Veeam Backup & Replication every 6 hours and get updated backup policy settings. If you targeted a backup policy at the Veeam backup server and scheduled earlier than the next connection to Veeam Backup & Replication, this backup policy will get updated backup policy settings at the next backup policy session start. To learn more about protection groups for pre-installed Veeam Agents, see [Protection Group Types](agents_protection_groups_types.md).

If you want to apply backup policy immediately, you must synchronize Veeam Agent with Veeam Backup & Replication from the Veeam Agent computer side manually. To learn more, see [Applying Protection Group Configuration to Veeam Agent for Microsoft Windows](deploy_agent_windows.md#configure).

[![Review Backup Policy Settings](images/agent_policy_summary_web.webp)](images/agent_policy_summary_web.webp "Review Backup Policy Settings")

Page updated 2026-07-16


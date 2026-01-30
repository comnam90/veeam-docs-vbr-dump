---
title: "Backup Policy Application Methods"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_policy_apply.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# Backup Policy Application Methods


To ensure that settings of Veeam Agent backup jobs on protected computers are up-to-date and do not differ from backup settings specified in the backup policy, Veeam Backup & Replication regularly applies the backup policy to protected computers.

|  |
| --- |
| TIP |
| You can also apply the backup policy to protected computers manually, if needed. To learn more, see [Applying Backup Policy to Protected Computers](agent_policy_apply.md). |

There are two methods to start the policy application process:

* By Veeam Backup & Replication

Veeam Backup & Replication applies the backup policy to protected computers at the following events:

* At the time when the backup policy is created.
* At the time when you start the backup process manually in the Veeam Backup & Replication console.
* At the time when Veeam Backup & Replication performs scheduled rescan of protection groups added to the backup policy. Veeam Backup & Replication automatically rescans a protection group upon schedule specified in the protection group settings.

|  |
| --- |
| NOTE |
| Keep in mind that Veeam Backup & Replication cannot apply backup policy to protection groups for pre-installed Veeam Agents and their members. For members of such protection groups, the policy application process can be started only by Veeam Agent. |

* By Veeam Agent

The Veeam Agent service running on a protected computer regularly synchronizes with Veeam Backup & Replication and checks whether job settings obtained from the backup policy are up-to-date and updates backup job settings, if necessary. Veeam Agent performs the synchronization every 6 hours.

You can also synchronize Veeam Agent with Veeam Backup & Replication immediately running the following command from the Veeam Agent computer:

* For Veeam Agent for Microsoft Windows computers:

|  |
| --- |
| "C:\Program Files\Veeam\Endpoint Backup\Veeam.Agent.Configurator.exe" -syncnow |

* For Veeam Agent for Linux, Veeam Agent for Oracle Solaris, Veeam Agent for IBM AIX and Veeam Agent for Mac computers:

|  |
| --- |
| veeamconfig mode syncnow |

During the synchronization session, Veeam Agent performs the following operations:

1. Connects to Veeam Backup & Replication and obtains from the Veeam Backup & Replication database information about backup policies to which the Veeam Agent computer was added.
2. Compares obtained backup policy settings with backup job settings in the Veeam Agent database. If the settings differ, Veeam Agent performs the following tasks:

* If backup policy settings and Veeam Agent backup job settings do not match, Veeam Agent updates backup job settings in its database.
* If the protected computer was added to a new backup policy, Veeam Agent creates a new backup job on the protected computer.
* If the protected computer was removed from the backup policy, Veeam Agent removes the Veeam Agent backup job on the protected computer.



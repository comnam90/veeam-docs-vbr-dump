---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_win_before_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you create a Veeam Agent backup policy in the Veeam Backup & Replication web UI, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers and workstations that you plan to add to the Veeam Agent backup policy. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.

|  |
| --- |
| NOTE |
| The Veeam Cloud Connect repository is not supported as a backup destination in the Veeam Backup & Replication web UI. |

Veeam Agent backup policies have the following limitations:

* Veeam Agent for Microsoft Windows does not back up data to which symbolic links are targeted. It only backs up the path information that the symbolic links contain. After restore, identical symbolic links are created in the restore destination.

* You cannot add a Veeam Agent computer protected by a backup job managed by the backup server to a Veeam Agent backup policy. To add such a computer to a Veeam Agent backup policy, first remove the computer from the backup job managed by the backup server.

Page updated 2026-07-14


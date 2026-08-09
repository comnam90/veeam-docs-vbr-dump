---
title: "Rescanning Protected Computer"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protected_computers_rescan.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Rescanning Protected Computer


You can rescan protected computers added to the inventory. The rescan operation may be required, for example, if you want to refresh information about the protected computer in the Veeam Backup & Replication database. During the rescan operation, Veeam Backup & Replication communicates to Veeam Installer Service running on the protected computer, retrieves information about the computer and stores this information to the configuration database.

Keep in mind that rescan is not available for protection groups for pre-installed Veeam Agents and their members. Veeam Agents installed on computers included in such protection groups connect to Veeam Backup & Replication every 6 hours and provide information about the Veeam Agent computer. If necessary, you can synchronize Veeam Agent with Veeam Backup & Replication running a command from the Veeam Agent computer. To learn more, see [Backup Policy Application Methods](agents_policy_apply.md).

|  |
| --- |
| NOTE |
| During the rescan of a separate protected computer, Veeam Backup & Replication does not perform [deployment operations](agents_protection_group_options.md) specified in the protection group settings. To perform the deployment operations, [rescan the protection group](agents_protection_group_rescan.md). |

You can rescan a protected computer in the following ways:

* [Rescanning Protected Computer Using Console](#console)
* [Rescanning Protected Computer Using Web UI](#webui)

Rescanning Protected Computer Using Veeam Backup & Replication Console

To rescan a protected computer in the Veeam Backup & Replication console:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node and select the necessary protection group.
3. In the working area, select the computer and click Rescan on the ribbon or right-click the computer and select Rescan.

[![Rescan Computer](images/protected_computer_rescan.webp)](images/protected_computer_rescan.webp "Rescan Computer")

Rescanning Protected Computer Using Veeam Backup & Replication Web UI

To rescan a protected computer in the Veeam Backup & Replication web UI:

1. In the management pane, click Protection Groups.
2. Select the protection group that contains the necessary computer.
3. In the working area, select the check box next to the computers and click Rescan on the toolbar. Alternatively, right-click the computer and select Rescan.

[![Rescan Computer](images/protected_computer_rescan_web.webp)](images/protected_computer_rescan_web.webp "Rescan Computer")

Page updated 2026-07-06


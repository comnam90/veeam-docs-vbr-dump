---
title: "Starting and Stopping Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_start_stop.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Starting and Stopping Backup


You can manually start backup on Veeam Agent computers added to the backup policy, for example, if you want to create an additional restore point in the backup chain and do not want to change the backup schedule. You can also stop the backup process, for example, if processing of a Veeam Agent computer is about to take long, and you do not want the backup process to produce load on the production environment during business hours.

When you start the backup process for a backup policy, Veeam Backup & Replication applies the policy to Veeam Agent computers and sends a command to start backup jobs on these computers.

When you stop the backup process for a backup policy, Veeam Backup & Replication does not apply the policy to Veeam Agent computers and immediately sends a command to stop backup jobs on these computers.

Veeam Backup & Replication does not check whether connection to Veeam Agent computers is active at the time when the command is sent. Keep in mind that the start or stop operation will be performed only on those computers that received the command from the backup server.

Keep in mind that you cannot start or stop the backup process for protection groups for pre-installed Veeam Agents and their members. Veeam Agent computers included in such protection groups will be skipped and Veeam Backup & Replication will display a warning message in a backup policy session statistics.

You can start or stop backup on Veeam Agent computers added to a backup policy in one of the following ways:

* [Using Veeam Backup & Replication Console](#console)
* [Using Veeam Backup & Replication Web UI](#webui)

Starting and Stopping Backup Using Veeam Backup & Replication Console

To start or stop backup on Veeam Agent computers added to the backup policy:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the backup policy and do one of the following:

* To start backup, click Start on the ribbon or right-click the policy and select Start.
* To stop backup, click Stop on the ribbon or right-click the policy and select Stop. In the displayed window, click Yes.

|  |
| --- |
| TIP |
| You can also start a Veeam Agent backup job directly on a protected computer from the Veeam Agent user interface. |

[![Starting and Stopping Backup](images/agent_policy_start.webp)](images/agent_policy_start.webp)

Starting and Stopping Backup Using Veeam Backup & Replication Web UI

To start or stop backup on Veeam Agent computers added to the backup policy:

1. In the management pane, click Jobs.
2. Select the check box next to the necessary backup policy and do one of the following:

* To start backup, click Start on the toolbar or right-click the policy and select Start.
* To stop backup, click Stop on the toolbar or right-click the policy and select Stop. In the Stop Job window, click Yes.

[![Start or Stop Backup](images/agent_policy_start_stop_web.webp)](images/agent_policy_start_stop_web.webp "Start or Stop Backup")

Page updated 2026-07-28


---
title: "Rescanning Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_rescan_appliance.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Rescanning Appliances


If a backup appliance becomes unavailable, you can rescan the appliance:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to Managed Servers.
3. Select the necessary backup appliance and click Rescan appliance on the ribbon.

Alternatively, you can right-click the appliance and select Rescan.

1. In the opened window, click Yes.

Veeam Backup & Replication will remove all data collected from the appliance configuration database. Then, Veeam Backup & Replication will recollect session results for the past 48 hours, as well as information on all snapshots, backups and policies.

|  |
| --- |
| Note |
| The rescan operation cannot be performed for available backup appliances and appliances that require upgrade. To learn how to upgrade backup appliances, see [Upgrading Appliances Using Console](aws_upgrade_appliance_console.md). |

[![Rescan appliance](images/aws_server_sync.webp)](images/aws_server_sync.webp "Rescan appliance")

Page updated 2026-05-20


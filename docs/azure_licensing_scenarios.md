---
title: "Scenarios"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_licensing_scenarios.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Scenarios


Backup appliances managed by a Veeam Backup & Replication server use the same license that is installed on the backup server. To learn what types of licenses and licensing models are incorporated in Veeam solutions, see:

* The [Licensing](licensing.md)
* The Veeam Backup & Replication Veeam Cloud Connect Guide, section [Licensing for Service Providers](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_hosting_licenses.html)

Licensing of New Backup Appliances

When you [deploy a new backup appliance](azure_deploying_appliance.md) from the Veeam Backup & Replication console, workloads start consuming license units from the license installed on the backup server after you create and run backup policies. After you remove the appliance from the backup infrastructure, Veeam Backup & Replication stops counting backed-up workloads and Veeam Plug-in for Microsoft Azure switches to the Free edition that allows you to protect up to 10 workloads free of charge.

|  |
| --- |
| Note |
| When you [connect to an existing backup appliance](azure_adding_appliance_console.md), the license installed on the appliance is replaced with the license installed on the backup server. However, protected instances start consuming license units from the license installed on the backup server only after the backup policy sessions run on the connected appliance. After you remove the appliance from the backup infrastructure, Veeam Backup & Replication stops counting backed-up workloads. The appliance continues using the license that was used before you added the appliance to the backup infrastructure. |

Licensing When Connection to Veeam Backup & Replication is Lost

Backup appliances store information on protected workloads licensed by Veeam Backup & Replication. This information allows you to back up workloads even if the connection between the backup appliance and backup server is lost. However, the following conditions must be met:

* The workload must have already been licensed by the backup server.
* The workload must be listed as licensed on the backup appliance side. For more information, see [Revoking License Units](https://helpcenter.veeam.com/docs/vbazure/guide/license_revoke.html?ver=60).
* The connection must be lost not more than 31 days ago.

Note that the loss of connection with Veeam Backup & Replication does not affect restore processes and creating of snapshots manually.

Page updated 2026-07-01


---
title: "License Management"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_oracle_license_management.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# License Management

In this article

If you plan to use Veeam Plug-Ins with Veeam Backup & Replication, you must install a valid license in Veeam Backup & Replication. The license must include a sufficient number of instances to protect the application servers or databases managed by Veeam Plug-Ins. To learn more about instance licensing, see [Veeam Licensing Policy](https://www.veeam.com/legal/licensing-policy.html#instance-conversion).

Veeam Plug-In checks license validity with Veeam Backup & Replication during backup operations. If a licensing issue occurs, the backup job fails. Veeam Backup & Replication tracks all licensed plug-in instances. It groups instances with the same BIOS UUID and consumes only one license for each group. Veeam Backup & Replication assigns the license to the workload with the highest value. For example, if both a VM and a plug-in use the same UUID, only one license is consumed.

Veeam Backup & Replication frees the license instance when you revoke a plug-in instance, such as after removing a backup job or deleting a host. If another Veeam product with the same UUID exists, that product may begin to use the released license.

|  |
| --- |
| Note |
| Veeam Plug-In and Veeam Backup & Replication log all license assign and revoke events for audit and troubleshooting. Veeam licensing logic ensures that only one license is consumed per host or group, even when multiple Veeam products are installed on the same host. |

Page updated 11/4/2025

Page content applies to build 13.0.1.1071

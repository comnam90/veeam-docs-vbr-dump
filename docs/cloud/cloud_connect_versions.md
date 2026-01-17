---
title: "Veeam Product Versions"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_versions.html"
last_updated: "11/24/2025"
product_version: "13.0.1.1071"
---


In this article

The SP and tenants can run different versions of Veeam Backup & Replication on their Veeam backup servers. Veeam products on the SP and tenant side must meet the following requirements:

* Veeam Backup & Replication versions must support the Veeam Cloud Connect functionality.
* The SP Veeam backup server can run the same or later version of Veeam Backup & Replication than the tenant Veeam backup server. The SP backup server cannot run an earlier version of Veeam Backup & Replication than the tenant backup server.

This applies to major product versions. Within Veeam Backup & Replication version 13, the SP and tenant can use any product build later that 13.0.1.180. It is recommended, however, that the SP and tenant install latest hotfixes and updates on the backup server.

* Veeam Backup & Replication 13.0.1 running on the SP backup server is compatible with the following versions of Veeam products running on the tenant side:

* Veeam Backup & Replication 12.3.2 (starting from 12.3.2.3617) and 13.0.1 or later

|  |
| --- |
| Note |
| Veeam Backup & Replication 13.0.0 is not supported. |

* Veeam Agent for Microsoft Windows 6.3.2 and later
* Veeam Agent for Linux 6.3.2 and later
* Veeam Agent for Mac 2.3.1 and later

If the SP or tenant plan to upgrade Veeam Backup & Replication to a later major product version, the upgrade process must start on the SP side. The upgrade process should be performed in the following way:

1. The SP upgrades Veeam Backup & Replication on the SP backup server. The upgrade procedure does not differ from a regular one. To learn more, see the [Upgrading to Veeam Backup & Replication 13 on Windows](https://helpcenter.veeam.com/docs/vbr/userguide/upgrade_vbr.html?ver=13) section in the Veeam Backup & Replication User Guide.
2. After Veeam Backup & Replication on the SP side is upgraded, the tenant can perform the upgrade procedure on the tenant backup server.

The sequence required for the upgrade to a later major product version does not apply to bug fixes and cumulative patch updates. In such scenarios, the update process can start on either the SP side or the tenant side.

Tenants who run earlier versions of Veeam Backup & Replication can continue using cloud resources provided to them by the SP who has upgraded Veeam Backup & Replication. However, some Veeam Cloud Connect functionality introduced in the current version of Veeam Backup & Replication may be not available to these tenants.

For installations with high loads (up to 1000 parallel tenant tasks), it is recommended that all tenants run the latest version of Veeam Backup & Replication and Veeam Agents.

Page updated 11/24/2025

Page content applies to build 13.0.1.1071

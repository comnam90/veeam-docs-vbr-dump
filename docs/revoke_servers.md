---
title: "Revoking License"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/revoke_servers.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Revoking License


You can revoke licenses from protected workloads or licensed hosts, and re-apply them to other objects that you plan to protect. License revoking can be helpful, for example, if a licensed host goes out of service or you do not want to protect some workloads anymore.

|  |
| --- |
| Note |
| If you manually revoke license instances allocated for an unstructured data source, the next run of the unstructured data backup job that protects this data source will trigger the recalculation of the data source protected size and reallocation of license instances that Veeam Backup & Replication will consume. For more information, see the [Instance Consumption for Object Storage Backup, File Backup and File to Tape Jobs](nas_licensing.md) section. |

You can revoke the consumed license from protected workloads in one of the following ways:

* [Revoking a license using the Veeam Backup & Replication console](revoke_license_console.md)
* [Revoking a license using the Veeam Backup & Replication web UI](revoke_license_web.md)



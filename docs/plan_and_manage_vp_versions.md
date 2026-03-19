---
title: "Supported Plug-In Versions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plan_and_manage_vp_versions.html"
last_updated: "3/12/2026"
product_version: "13.0.1.2067"
---

# Supported Plug-In Versions


Periodically, Veeam releases a new version of Veeam Backup & Replication that contains new features and bug fixes. The release package also contains a new version of Veeam Plug-Ins.

Veeam Backup & Replication 13 supports different versions of Veeam Plug-In depending on which OS is running on the backup server:

* Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported.
* Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.

|  |
| --- |
| Note |
| Veeam Plug-In for Microsoft SQL Server supports the managed operation mode starting with version 13.0.1.180-1. If you have an earlier supported version of Veeam Plug-In for Microsoft SQL Server, you must upgrade it. You can upgrade Veeam Plug-In [on the Microsoft SQL Server](update_mssql_plugin.md) or you can add the machine to the protection group and enable auto-update for Veeam components [during protection group configuration](protection_group_create.md). After that, you can start using Veeam Plug-In in the managed operation mode. |

Note that Veeam Backup & Replication must be the same or later than the version of Veeam Plug-In. If you want to use the latest functionality, you must upgrade both Veeam Backup & Replication and Veeam Plug-In to the latest version. If you use an earlier Veeam Plug-In build, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474).

Veeam Backup & Replication version 13 (build 13.0.2.2067-1) comes with the following Veeam Plug-Ins stored in the ISO file:

* Veeam Plug-In for SAP HANA
* Veeam Plug-In for Oracle RMAN
* Veeam Plug-In for SAP on Oracle
* Veeam Plug-In for Microsoft SQL Server



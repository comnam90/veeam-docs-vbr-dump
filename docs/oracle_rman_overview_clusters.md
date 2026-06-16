---
title: "Support for Cluster Solutions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_rman_overview_clusters.html"
last_updated: "6/15/2026"
product_version: "13.0.2.29"
---

# Support for Cluster Solutions


Depending on the operation mode, Veeam Plug-In for Oracle RMAN supports backup and restore of Oracle databases that operate in clusters based on one of the following solutions:

Support for Cluster Solutions

| Solution | Standalone Mode | Managed Mode |
| Oracle Exadata, Oracle Database Appliance, Oracle RAC | Supported | Supported |
| Oracle Data Guard | Supported | Not supported |

To learn more about operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md).

Considerations and Limitations

Before you protect a database in a cluster, consider the following:

* It is recommended to install Veeam Plug-In for Oracle RMAN on each machine that is responsible for the backup operations. If the plug-in is not installed on all cluster nodes, the backup process may fail when RMAN selects another node.
* Veeam Plug-In supports parallel execution of all operations supported by Oracle RMAN: backup, restore, crosscheck, remove. This applies to execution of these commands on one or multiple databases residing on one or multiple cluster nodes.

* The progress bar of a running Oracle database backup job is not available for Oracle databases that operate in clusters based on Oracle RAC.

* If you use Veeam Explorer for Oracle to restore an Oracle database from a cluster deployment, consider the limitations in [Restore from RMAN Plug-in Backups](veor_considerations.md#restore-rman).



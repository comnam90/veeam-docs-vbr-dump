---
title: "Support for Cluster Solutions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_rman_overview_clusters.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Support for Cluster Solutions


Depending on the operation mode, Veeam Plug-In for Oracle RMAN supports backup and restore of Oracle databases that operate in clusters based on one of the following solutions:

Support for Cluster Solutions

| Solution | Standalone Mode | Managed Mode |
| Oracle Exadata, Oracle Database Appliance, Oracle RAC | Supported | Supported |
| Oracle SEHA, Oracle Data Guard | Supported | Not supported |
| Oracle Fail Safe, Pacemaker and Corosync, Red Hat High Availability Add-On | Supported. The configuration of the customServerName parameter is required. For details, see [Backup of Clusters that Require Custom Server Name](oracle_rman_overview_clusters.md#custom). | Not supported |

To learn more about operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md).

Considerations and Limitations

Before you protect a database in a cluster, consider the following:

* It is recommended to install Veeam Plug-In for Oracle RMAN on each machine that is responsible for the backup operations. If the plug-in is not installed on all cluster nodes, the backup process may fail when RMAN selects another node.
* Veeam Plug-In supports parallel execution of all operations supported by Oracle RMAN: backup, restore, crosscheck, remove. This applies to execution of these commands on one or multiple databases residing on one or multiple cluster nodes.

* The progress bar of a running Oracle database backup job is not available for Oracle databases that operate in clusters based on Oracle RAC and Oracle SEHA.

* If you use Veeam Explorer for Oracle to restore an Oracle database from a cluster deployment, consider the limitations in [Restore from RMAN Plug-in Backups](veor_considerations.md#restore-rman).

Backup of Clusters That Require Custom Server Name

To back up certain clusters, you must update the Veeam Plug-In configuration files stored on the machines. In these Veeam Plug-In configuration files, you must specify a custom name for all machines that participate in backup and restore. The custom name must be the same on all machines. Cluster deployments that require such an operation are based on the following solutions:

* Oracle Fail Safe
* Pacemaker and Corosync
* Red Hat High Availability Add-On

To assign a custom name to the machine, update the Veeam configuration XML file as follows:

1. Open the Veeam configuration XML file. The path to the file differs depending on the OS of the machine where Veeam Plug-In is installed:

* On machines running Linux or Unix OS: /opt/veeam/VeeamPluginforOracleRMAN/veeam\_config.xml
* On machines running Windows OS: %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\veeam\_config.xml

1. Add the customServerName parameter entry to the <PluginParameters /> line in the file:

|  |
| --- |
| <PluginParameters customServerName="name" /> |

where <name> is the custom name of the machine.

For example:

|  |
| --- |
| <PluginParameters customServerName="cluster001" /> |

After you add this parameter on each machine, Veeam Plug-In will use the specified custom name for the whole group of machines.

1. When you configure application backup jobs on the machines, make sure that the following requirements are met:

* Veeam Plug-In on all machines back up to the same Veeam backup repository.
* All machines authenticate against Veeam Backup & Replication using the same credentials.

After these steps, you can back up databases in a cluster. In case you switch your active system from the current primary system to the secondary system, backup chains will continue seamlessly using existing backup files. Although you do not need to perform a full database backup after you switch the system, we recommend to perform it.

Page updated 2026-07-08


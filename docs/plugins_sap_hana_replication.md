---
title: "Support for SAP HANA System Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_hana_replication.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Support for SAP HANA System Replication


Veeam Plug-In for SAP HANA operating in the standalone mode supports backup and restore of SAP HANA databases that operate as parts of SAP HANA System Replication. For more information about SAP HANA System Replication, see [SAP documentation](https://help.sap.com/docs/SAP_HANA_PLATFORM/4e9b18c116aa42fc84c7dbfd02111aba/afac7100bc6d47729ae8eae32da5fdec.html?locale=en-US).

Backup of SAP HANA System Replication

To back up databases that operate as parts of SAP HANA System Replication, do the following:

1. Install and configure Veeam Plug-In on each machine participating in SAP HANA System Replication. For details, see [Installing Veeam Plug-In for SAP HANA](installing_plugin_sap_hana.md) and [Configuring Plug-In for SAP HANA](configure_sap_hana_plugin.md).
2. In the Veeam Plug-In configuration files stored on the machines, assign the same custom name to each machine.

To assign a custom name to the machine, do the following:

1. On the machine with Veeam Plug-In, open the /opt/veeam/VeeamPluginforSAPHANA/veeam\_config.xml file.
2. Add the customServerName parameter entry to the <PluginParameters /> line in the file:

|  |
| --- |
| <PluginParameters customServerName="<name>" /> |

where <name> is the custom name for the group of the machines that participate in SAP HANA System Replication.

For example:

|  |
| --- |
| <PluginParameters customServerName="cluster001" /> |

After you add this parameter on each machine, Veeam Plug-In will use the specified custom name for the whole group of machines.

1. Back up databases on the machines in SAP HANA System Replication considering the following requirements:

* All machines must use the same Veeam backup repository.
* All machines must authenticate against Veeam Backup & Replication using the same credentials.

For details, see [Database Protection](sap_hana_backup.md).

After these steps, in case you switch your active system from the current primary system to the secondary system, backup chains will continue seamlessly using existing backup files. Although you do not need to perform a full database backup after you switch the system, we recommend to perform it.

|  |
| --- |
| Important |
| If you have not assigned a custom name to machines in SAP HANA System Replication, consider the following:   * After each takeover, you must re-configure Veeam Plug-In to continue creating backups. The reason is that SAP HANA does not allow you to back up databases located on replicas. You can back up these databases only after a takeover. * After each takeover and Veeam Plug-In re-configuration, you must perform full database backup at least once, so that SAP HANA starts to create automatic log backups. |

Restore of SAP HANA System Replication

The restore after takeover differs depending on the way you configured Veeam Plug-Ins on machines that participate in SAP HANA System Replication:

* If you have assigned a custom name to machines in SAP HANA System Replication as described in [Backup of SAP HANA System Replication](#backup), Veeam Plug-In treats all systems as one machine. As a result, you can restore database in the usual way. For details, see [Database Recovery](restoring_databases.md).
* If you have not assigned a custom name, Veeam Plug-In treats each system as an independent machine. After takeover, you must re-configure Veeam Plug-In to recognize the new primary system as the original system. As a result, you must perform the restore only in the following way:

1. On the machine with Veeam Plug-In, run the SapBackintConfigTool tool with the following parameter:

|  |
| --- |
| SapBackintConfigTool --set-backup-for-restore |

This command specifies the backup that Veeam Plug-In will use for restore. For details about the command, see [Restore to Another Server (System Copy)](restore_saphana_other_server.md).

1. Perform restore using a specified. For details, see [Database Recovery](https://helpcenter.veeam.com/docs/vbr/userguide/restoring_databases.html).

If then you want to restore from a backup created in a new backup chain, you must use the --set-backup-for-restore parameter again to select a new backed-up machine as a source for restore.



---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_limitations.html"
last_updated: "2/6/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


This section contains information on limitations for the HA cluster.

General Limitations for HA Cluster

Consider the following general limitations for the HA cluster:

* To be able to use the HA cluster, you must install the Veeam Data Platform Premium License. You must apply this license to the Veeam software appliance that you plan to use as the primary node. For more details about all license types, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).

|  |
| --- |
| Note |
| You cannot use earlier iterations of the Veeam Universal License (for example, Veeam Availability Suite), unless you upgrade your license to the Veeam Data Platform Premium License. To upgrade the license, use the [Update license](license_update_manual.md) option. |

* Before you assemble the HA cluster, make sure that both nodes have the same DNS suffixes and correct DNS addresses. Otherwise, Veeam Backup & Replication will not be able to resolve infrastructure servers on both nodes.
* Veeam Backup & Replication does not automatically install [Universal Storage API integrated systems](universal_storage_integration_api.md) on an HA cluster. You must install the necessary Universal Storage API integrated system plug-in on every node. For more information, see [Installing and Updating Plug-ins on Linux-Based Backup Server](storage_install_plugin_linux.md).

* You cannot use local repositories (the default repository located on your backup server) within the HA cluster. Before you configure an HA cluster, you must add a new backup repository to your backup infrastructure and then remove the local repository from it.

|  |
| --- |
| Note |
| Consider the following:   * By default, configuration backups are located in the local backup repository. If you want to create configuration backups for your nodes, you must specify a different backup repository to store these backups. For more information, see [Scheduling Configuration Backups](vbr_config_schedule.md). * If you use a scale-out backup repository, ensure that it does not use local repositories as performance extents. |

* Veeam Backup & Replication does not automatically install private fixes. You must do it manually using the Veeam Host Management console for every HA node. For more information, see [Installing Private Hotfixes](update_appliance_install_updates.md).

|  |
| --- |
| Note |
| We recommend that you install private fixes on both nodes, so that they have the same configuration. |

* You cannot use the [Veeam Host Management console](hmc_about.md) and the [Veeam Backup & Replication Web UI](vbr_web_console.md) to manage an HA cluster.

|  |
| --- |
| Tip |
| You can use the  [Veeam Host Management console](hmc_about.md) to manage each HA node individually. |

* Both HA nodes must have the same version of Veeam Backup & Replication installed.
* You can use an existing backup server as a primary node for your HA cluster. Do not use the backup server that you are already using as the secondary node. Otherwise, after you assemble the HA cluster, its configuration database will be deleted and replaced with the configuration database of the primary HA node.
* Before you [regenerate self-signed certificates](self_signed_tls.md), ensure that both cluster nodes are online and the cluster is fully functional. You will not be able to regenerate the certificates while one of the nodes is down.
* The events that Veeam Backup & Replication writes and sends to the [syslog server](syslog_servers.md) do not contain events for the HA cluster reconfiguration and a failover.

* [Veeam Backup Enterprise Manager] If a backup server is added to Enterprise Manager, you must re-add it using the cluster virtual IP address or cluster DNS name after assembling the cluster. If you do not re-add the backup server, Enterprise Manager will not be able to collect data from it after a switchover.

Kerberos Environment Limitations for HA cluster

Consider the following limitations for the HA cluster with the Kerberos environment:

* Ensure that the cluster IP is allowed to communicate to the ports used for Kerberos authentication. For more information, see the [Ports](used_ports.md#kerberos) section.
* To configure an HA cluster with Kerberos, follow these steps:

1. Join both nodes to a domain where Kerberos authentication is configured. For more information, see [Managing Domain Settings](hmc_configure_domain.md).
2. Submit the request to enable the High Availability option for both Veeam Software Appliance nodes.
3. Create a .keytab file and import it to the primary node using the [Veeam Host Management Web UI](hmc_access.md). For more information, see [Creating Keytab File](high_availability_configuration_byb.md).
4. Assemble the HA cluster.

|  |
| --- |
| Note |
| If you omit one of these steps or do not follow this order, the HA cluster may have communication issues between the primary and secondary nodes. For more information on configuring the cluster with Kerberos, see [Assembling HA cluster Prerequisites](high_availability_configuration_byb.md). |

* If you use Kerberos authentication, you must reserve a static IP address for the cluster that can contact the Kerberos Key Distribution Center (KDC).
* During a failover, the [Log in as current user](web_ui_logon.md#current) option in the Veeam Backup & Replication web UI is not supported. You must specify credentials in plain text.
* If you [remove a node from a domain](hmc_configure_domain.md) where Kerberos authentication is configured after the HA cluster is assembled, it will result in connectivity issues between the HA nodes. If you need to remove a node from a domain, first disassemble the cluster, then remove both nodes from the domain, and then recreate the cluster.

HA Cluster Network Limitations

Consider the following network limitations for the HA cluster:

* Before you assemble the HA cluster, make sure that both nodes have the same DNS suffixes and correct DNS addresses. Otherwise, Veeam Backup & Replication will not be able to resolve infrastructure servers on both nodes. Ensure that the HA cluster hostname resolves to the correct IP by both HA nodes.
* The machines that you use as Linux-based backup servers must allow inbound and outbound traffic on the ports listed in the [Ports](used_ports.md#copnfigurationdb) section. Ensure that these ports are opened for the cluster IP to enable proper cluster operations.
* The HA cluster does not synchronize DNS suffixes between HA nodes. You must add the suffixes for both nodes in the [Veeam Host Management console](hmc_about.md).

* You must use static IP addresses for the HA nodes and for a cluster virtual IP address.

* The hosts that you plan to use as the HA nodes must be in the same subnet.
* After you disassemble your HA cluster, the static IP address of the cluster remains assigned to the HA primary node.

* If you want to include the DNS name of the HA cluster in the self-signed certificate, you must regenerate this certificate after you assemble the cluster. After that, the cluster DNS name will be added to the alternative names. Ensure that both cluster nodes are online and the cluster is fully functional.

* Ensure that the TCP protocol is opened on both primary and secondary nodes. Otherwise, Veeam Backup & Replication will not be able to send WAL logs of the PostgreSQL database to the secondary node.
* Ensure that you use only one type of IP address—either IPv4 or IPv6—for the HA cluster configuration. If you configure HA cluster with a mix of both IPv4 and IPv6 addresses, the HA cluster will not operate.

HA Cluster Configuration Database Limitations

Consider the following configuration database limitations for the HA cluster:

* HA cluster supports only PostgreSQL as a configuration database.
* You cannot assemble an HA cluster if your Linux-based backup servers have PostgreSQL databases configured on a remote host. HA cluster supports only PostgreSQL databases configured on a local host of the HA node.
* After you assemble the cluster, do NOT modify the PostgreSQL database configuration to host the database on a remote server.
* Veeam Backup & Replication does not support configuration restore to an HA cluster.
* The configuration backup does not contain information about an HA cluster. You can perform a configuration restore of the HA cluster only to a standalone Veeam Backup & Replication.

HA Cluster Synchronization Limitations

Consider the following synchronization limitations for the HA cluster:

* Veeam Backup & Replication synchronizes job scripts, pre-freeze and post-thaw scripts only if they are located in the /var/lib/veeam/scripts directory. Currently, it is not possible to synchronize scripts from the different directories.
* Veeam Backup & Replication does not synchronize Veeam appliance users between nodes of an HA cluster. If you plan to use several users to manage your HA cluster, you must create these users on each HA node. For more information on creating users, see [Configuring Users](hmc_configure_users.md).

* Veeam Backup & Replication synchronizes only the global update configuration settings of the Veeam Updater service. If you need to set custom update configuration settings, you must set them up for each node. For more information, see [Configuring Updates](update_appliance_configure_updates.md).
* Veeam Backup & Replication does not synchronize the following data:

* Data located in the /var/lib/veeamdata/veeam/IRCache/ directory.
* Index of files and folders on the VM guest OS.
* Backup server logs. To get the logs for the necessary node, use the [Veeam Host Management Console](hmc_perform_maintenance_tasks.md).

HA Cluster Failover Limitations

Before you perform a failover, consider the following limitations:

* Before you initiate a failover, ensure that the primary node is offline and will not revert to online status during the failover. Otherwise, it may lead to split-brain scenarios.
* Kerberos authentication is not supported during failover to the secondary node. You must specify credentials in plain text.
* Veeam Backup & Replication does not support automatic failover of an HA cluster.

* If you initiate a failover while the secondary node is not synchronized with the primary node — for example, due to network issues — the secondary node database may lack information about the latest backup files created by the primary node. After the failover, you must rescan the backup repository to ensure the secondary node is updated with any backup files created while it was out of sync.
* To initiate a failover, you must use either the cluster virtual IP address or the IP address of the secondary node. You cannot initiate a failover using the cluster DNS name.

HA Cluster Switchover Limitations

Before you perform a switchover, consider the following limitations:

* It is crucial to prevent any scenario where either the primary or secondary node becomes offline (for example, due to power loss or network connectivity issues) during the switchover process. If either node goes and remains offline for the entire duration of the switchover, the HA cluster will be unable to recover. If this happens, contact [Veeam Customer Support](https://www.veeam.com/support.html).
* Veeam Backup & Replication does not support an automatic switchover of an HA cluster.
* During a switchover, Veeam Backup & Replication stops all jobs and services.

* [Instant Recovery to Hyper-V] Make sure you [finalize the Instant Recovery session](ir_finalize_hv.md) to Hyper-V before you start a switchover. During a switchover, Veeam Backup & Replication stops the Instant Recovery session. After that, the VM that Veeam Backup & Replication creates on the Hyper-V datastore and its snapshot are deleted. Once you connect to a cluster, Veeam Backup & Replication will start an Instant Recovery session again.

Disassembling HA Cluster Limitations

Before you disassemble an HA cluster, consider the following limitations:

* By default, you cannot use the secondary node as a standalone backup server after you disassemble an HA cluster, since it still contains the configuration files and certificates. To use it as a standalone backup server, you must [reinstall Veeam Infrastructure Appliance](linux_infrastructure_appliance_install.md).
* If you disassemble an HA cluster, you can use the secondary node again in the same cluster.



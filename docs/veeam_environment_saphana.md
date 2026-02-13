---
title: "Veeam Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_environment_saphana.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Veeam Environment Planning


The integration of SAP HANA and Veeam Plug-In requires additional environment planning. Before you deploy Veeam Plug-In, keep in mind the following requirements and limitations.

Hosting Environments and Backup Job Names

By default, Veeam Plug-In uses the server hostname to create a Veeam Backup & Replication job object and backup folder. To distinguish between servers with the same hostnames, you can assign custom names for these servers.

To assign a custom name, update the Veeam configuration XML file as follows:

1. On the machine with Veeam Plug-In, open the /opt/veeam/VeeamPluginforSAPHANA/veeam\_config.xml file.
2. Add the customServerName parameter entry to the <PluginParameters /> line in the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters customServerName="hostname.domain.tld" /> |

where <hostname.domain.tld> is the custom name of the server.

After adding this parameter, Veeam Plug-In will use the specified custom name of the server to name the backup job and backup folder.

For example:

|  |
| --- |
| <PluginParameters customServerName="srv01.tech.local" /> |

Alternatively, you can use the useFQDNInServerName parameter:

|  |
| --- |
| <PluginParameters useFQDNInServerName="true" /> |

After adding this parameter, Veeam Plug-In will use the fully qualified domain name (FQDN) of the server to name the backup job and backup folder.

Keep in mind that you must add the parameters to the existing line in the veeam\_config.xml file. If you create a new line with the same name as the existing line, Veeam Plug-In will consider parameters only in the first detected line. Other parameters will be ignored.

|  |
| --- |
| Important |
| For security reasons, it is recommended to use separate repositories for different customers and limit the Veeam Repository Authentication to the specific customer. |

Veeam User Management

Veeam Plug-In for SAP HANA uses the Windows authentication methods of the Veeam Backup & Replication server to establish a connection to this server and to the target backup repository. It is recommended to create one specific user for each Veeam Plug-In server or for each scale-out cluster.

In case of future manual changes to the user account, the new user must have at least the Veeam Backup Operator and Veeam Restore Operator rights within the Veeam Backup & Replication user management. To learn how to assign Veeam Backup & Replication roles, see [Users and Roles](users_roles.md).

Network Traffic Encryption

Veeam Plug-In supports network traffic encryption rules set on the Veeam Backup & Replication side. By default, Veeam Plug-In automatically applies the traffic encryption rules. To decrease the processing load on the database server, you can disable network traffic encryption by ignoring the rules set on the Veeam Backup & Replication side.

To ignore network traffic encryption rules, do the following:

1. Locate the Veeam configuration XML file: /opt/veeam/VeeamPluginforSAPHANA/veeam\_config.xml.
2. Add the following parameter to the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters IgnoreVBRNetworkRules="true" /> |

For details on traffic encryption, see [Enabling Traffic Encryption](enable_network_encryption.md).

SAP HANA Backup Channels and Veeam Repository Task Slots

By default, SAP HANA uses one channel per data backup operation. You can configure SAP HANA to use additional channels. When multiple channels are used, SAP HANA distributes the data equally across available channels.

Keep in mind that the number of SAP HANA channels must be equal to the number of available task slots in the repository. For details on task slot limitations, see [Limitation of Concurrent Tasks](limiting_tasks.md#task-limitation-for-backup-repositories).

When using multiple channels in parallel, the data flow between SAP HANA and the source Veeam Data Mover is faster. This also improves overall backup performance. However, consider that using multiple channels uses more resources on the SAP HANA server, the network, the backup source, the target disk systems, and in the Veeam backup repository. To learn more about backup repository resource usage and limitations, see [Veeam Backup Repositories](sap_repos.md).

To control the number of parallel channels used for each SAP HANA Backint instance, edit the parallel\_data\_backup\_backint\_channels parameter in the SAP HANA global.ini file. For detailed instructions on how to edit the number of channels used in parallel, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/18db704959a24809be8d01cc0a409681.html?locale=en-US).

|  |
| --- |
| Note |
| The application of multiple streaming channels applies to all data backup services larger than 128 GB. Data backup services smaller than 128 GB use only one channel. |

If you use a dedicated backup repository for Veeam Plug-In backups, the following hardware resources are recommended and are based on tests on Skylake processors:

* SAP HANA server: 1 CPU core and 200 MB of RAM per currently used channel.
* Backup repository server: 1 CPU core and 1 GB of RAM per 5 currently used channels.

If you use the same backup repository for Veeam Plug-In backups and backups created by Veeam Backup & Replication or Veeam Agents, consider adding the mentioned above hardware resources based on usual load on your backup repository.

To learn more about the requirements for backup repositories, see [Backup Server System Requirements](system_requirements.md#repo).

Additionally, consider the following limitations when using of multiple channels:

* It is not recommended to use more than 64 channels in parallel as the overhead will reduce individual channel performance. Set the max\_recovery\_backint\_channels setting in global.ini to 64 or below depending on available hardware resources.
* It is recommended to use a separate backup repository for Veeam Plug-In backups.
* If you want to improve backup performance, the SAP HANA buffer must be increased for additional used channels. For details, consult with your SAP HANA database administrator.

* SAP HANA can back up individual databases and tenants in parallel. To optimize resources, you can back up databases sequentially.
* If there are not enough available repository task slots, SAP HANA waits till repository task slots become available.
* During restore, the order of repository task slots is ignored, and channels are used as requested by SAP HANA.

* Veeam Backup & Replication server: during manual metadata operations such as [import of backup files](import_backup_files.md), the Veeam Backup & Replication server needs additional 15 GB of RAM per 1 million files located in the same backup job folder.

Example 1: Backing up all databases in parallel

In this example, the system has 2 tenant databases, each database has 4 services. The databases are backed up in parallel. The SAP HANA channel setting is 6. The following channels are used:

* Up to 4 channels are used by SYSTEMDB and its 4 services (all below 128 GB).
* Up to 6 channels are used for the index service of the tenant database 1 (the database is bigger than 128 GB).
* Up to 3 channels are used for the rest of the 3 remaining services of the tenant database 1 (all below 128 GB).
* Up to 6 channels are used for the index service of the tenant database 2 (the database is bigger than 128 GB).
* Up to 3 channels are used for the rest of the 3 remaining services of the tenant database 2 (all below 128 GB).
* If the log backups are below 128 GB, you must reserve at least 3 channels for the log backup of SYSTEMDB, tenant database 1, and tenant database 2. These log backups are started automatically on their own schedule or when the maximum file size of the log file is reached.

In total, 27 channels were used. For backup processes of all databases started in parallel, up to 27 task slots must be available.

Example 2: Backup of all databases sequentially

In this example, the system has 2 tenant databases, each database has 4 services. The databases are backed up sequentially. The SAP HANA channel setting is 6. The following maximum repository task slots and SAP channels are used:

* Up to 6 channels are used for the index service of a tenant database (the database is bigger than 128 GB).
* Up to 3 channels are used for the rest of the 3 remaining services of the same tenant database (all below 128 GB).
* If the log backups are below 128 GB, you must reserve at least 3 channels for the log backup of SYSTEMDB, tenant database 1, and tenant database 2. These log backups are started automatically on their own schedule or when the maximum file size of the log file is reached. Assuming that the log file backups are below 128 GB and do not use additional channels.

In total, 12 channels were used. For backup processes of sequential started database backups, up to 12 task slots must be available.

Additional Files to Back Up

Veeam Plug-In for SAP HANA and SAP HANA do not include the respective configuration files in backups automatically. After the installation and configuration, consider the additional manual backup of the following configuration files:

* Veeam Plug-In configuration file: /opt/veeam/VeeamPluginforSAPHANA/veeam\_config.xml

* SAP HANA configuration files:

* /usr/sap/<SID>/SYS/global/hdb/custom/config
* /usr/sap/<SID>/<INSTANCE>/<FQDN>
* /usr/sap/<SID>/SYS/global/hdb/custom/config

To learn more about SAP HANA configuration files, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/c39a9abbbb57101496d4fade60e43503.html).



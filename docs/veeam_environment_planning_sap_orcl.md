---
title: "Veeam Environment Planning"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_environment_planning_sap_orcl.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Veeam Environment Planning

In this article

Integration of SAP on Oracle and Veeam Plug-In requires additional environment planning. When you deploy the plug-in, keep in mind the following requirements and limitations.

Hosting Environments and Backup Job Names

By default, Veeam Plug-In uses the Oracle server hostname to create a Veeam Backup & Replication job object and backup folder. To distinguish between servers with the same hostnames, you can assign custom names for these servers.

To assign a custom name, update the Veeam configuration XML file as follows:

1. On the machine with Veeam Plug-In, open the /opt/veeam/VeeamPluginforSAPOracle/veeam\_config.xml file.
2. Add the customServerName parameter entry to the <PluginParameters /> line in the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters customServerName="hostname.domain.tld" /> |

where <hostname.domain.tld> is a custom name of the server.

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

Network Traffic Encryption

Veeam Plug-In supports network traffic encryption rules set on the Veeam Backup & Replication side. By default, Veeam Plug-In automatically applies the traffic encryption rules. To decrease the processing load on the database server, you can disable network traffic encryption by ignoring the rules set on the Veeam Backup & Replication side.

To ignore network traffic encryption rules, do the following:

1. Locate the Veeam configuration XML file: /opt/veeam/VeeamPluginforSAPOracle/veeam\_config.xml.
2. Add the following parameter to the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters IgnoreVBRNetworkRules="true" /> |

For details on traffic encryption, see [Enabling Traffic Encryption](enable_network_encryption.md).

Veeam Backup & Replication Users and Roles

Veeam Plug-In for SAP on Oracle uses the Windows authentication methods of the Veeam Backup & Replication server to establish a connection to this server and to the backup target.

If this user will be later changed manually, the new user must have at least the Veeam Backup Operator and Veeam Restore Operator rights within the Veeam Backup & Replication user management. To learn how to assign Veeam Backup & Replication roles, see [Users and Roles](users_roles.md).

Parallel Data Streams and Backup Repository Task Slots

Any parallel data stream started by SAP Backint will use one backup repository task slot. It is recommended to carefully plan repository task slots, so that SAP Backint can work with multiple channels in parallel.

The following hardware resources are recommended based on tests on Skylake processors:

* SAP on Oracle server: 1 CPU core and a minimum of 200 MB of RAM per currently used channel. Note that resource consumption on the SAP on Oracle server depends on hardware and Oracle settings.
* Backup repository server: 1 CPU core and 1 GB of RAM per 5 currently used channels.

These resources are recommended only if you use a dedicated backup repository for Veeam Plug-In backups. If you use the same backup repository for Veeam Plug-In backups and VM backups created by Veeam Backup & Replication or Veeam Agents, consider adding the hardware resources based on usual load on your backup repository. For details on hardware requirements for a backup repository, see [Backup Server System Requirements](system_requirements.md#repo).

It is recommended to contact your Veeam system engineer to optimize the channel settings and resource allocation.

It is recommended to use a separate backup repository for Veeam Plug-In backups.

* Veeam Backup & Replication server: during manual metadata operations such as [import of backup files](import_backup_sap_orcl.md), the Veeam Backup & Replication server needs additional 15 GB of RAM per 1 million files located in the same backup job folder.

Limitation for SAP Detection on Different Host

Veeam Plug-In may not be able to detect SAP instances during the configuration if the Oracle Database and SAP central instance are running on different hosts. If you work with Veeam Plug-In in the managed mode, this configuration is not supported. If you work with Veeam Plug-In in the standalone operation mode, see [Configuring Plug-In for SAP on Oracle](configure_sap_orcl.md).

Page updated 11/28/2025

Page content applies to build 13.0.1.1071

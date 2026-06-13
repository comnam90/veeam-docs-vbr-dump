---
title: "Veeam Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_environment_saphana.html"
last_updated: "6/10/2026"
product_version: "13.0.2.29"
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

Additional Files to Back Up

Veeam Plug-In for SAP HANA and SAP HANA do not include the respective configuration files in backups automatically. After the installation and configuration, consider the additional manual backup of the following configuration files:

* Veeam Plug-In configuration file: /opt/veeam/VeeamPluginforSAPHANA/veeam\_config.xml

* SAP HANA configuration files:

* /usr/sap/<SID>/SYS/global/hdb/custom/config
* /usr/sap/<SID>/<INSTANCE>/<FQDN>
* /usr/sap/<SID>/SYS/global/hdb/custom/config

To learn more about SAP HANA configuration files, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/c39a9abbbb57101496d4fade60e43503.html).



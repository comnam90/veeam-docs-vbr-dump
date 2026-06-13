---
title: "Veeam Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_environment_planning_mssql.html"
last_updated: "6/10/2026"
product_version: "13.0.2.29"
---

# Veeam Environment Planning


Before you deploy Veeam Plug-In, keep in mind the following requirements and limitations.

Hosting Environments and Backup Job Names

By default, Veeam Plug-In generates names for backup jobs and backup folders according to the hosting environment where the backup job is created:

* For the standalone server, Veeam Plug-In generates names based on the server hostname.
* For the Microsoft SQL failover cluster, Veeam Plug-In generates names based on the Microsoft SQL server network name.
* For the Always On availability group, Veeam Plug-In generates names based on the group hostname.

You can set Veeam Plug-In to use a custom name instead of the default name. This may be helpful, for example, if you have servers with the same hostname in multiple environments.

To assign a custom name, update the Veeam configuration XML file as follows:

1. On the machine with Veeam Plug-In, open the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\veeam\_config.xml file.
2. Add the customServerName parameter entry in the Veeam configuration XML file: to the <PluginParameters /> line in the Veeam configuration XML file:

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

Network Traffic Encryption

Veeam Plug-In supports network traffic encryption rules set on the Veeam Backup & Replication side. By default, Veeam Plug-In automatically applies the traffic encryption rules. To decrease the processing load on the database server, you can disable network traffic encryption by ignoring the rules set on the Veeam Backup & Replication side.

To ignore network traffic encryption rules, do the following:

1. Locate the Veeam configuration XML file in the following location:

|  |
| --- |
| %PROGRAMFILES%\Veeam\VeeamPluginforMSSQL\veeam\_config.xml |

1. Add the following parameter to the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters IgnoreVBRNetworkRules="true" /> |

For details on traffic encryption, see [Enabling Traffic Encryption](enable_network_encryption.md).



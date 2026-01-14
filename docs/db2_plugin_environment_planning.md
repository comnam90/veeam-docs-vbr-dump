---
title: "Environment Planning"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_plugin_environment_planning.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Environment Planning

In this article

Before you deploy Veeam Plug-In, keep in mind the following requirements and limitations.

Hosting Environments and Backup Job Names

By default, Veeam Plug-In uses the hostname of the IBM Db2 machine or cluster to create a Veeam Backup & Replication job and backup folder. To distinguish between servers with the same hostnames, you can assign custom names to these servers.

To assign a custom name, update the Veeam configuration XML file as follows:

1. On the machine with Veeam Plug-In, open the /opt/veeam/VeeamPluginforDB2/veeam\_config.xml file.
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

Veeam Plug-In supports network traffic encryption rules set on the Veeam Backup & Replication side. By default, Veeam Plug-In for IBM Db2 automatically applies the traffic encryption rules. To decrease the processing load on the database server, you can disable network traffic encryption by ignoring the rules set on the Veeam Backup & Replication side.

To ignore network traffic encryption rules, do the following:

1. On the machine with Veeam Plug-In, open the /opt/veeam/VeeamPluginforDB2/veeam\_config.xml file.
2. Add the following parameter to the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters IgnoreVBRNetworkRules="true" /> |

For details on traffic encryption, see [Enabling Traffic Encryption](enable_network_encryption.md).

Page updated 11/28/2025

Page content applies to build 13.0.1.1071

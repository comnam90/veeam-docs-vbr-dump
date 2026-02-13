---
title: "Veeam Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_environment_planning.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Veeam Environment Planning


Before you deploy Veeam Plug-In, keep in mind the following requirements and limitations.

* [Hosting Environments](#hosting)
* [RMAN Channels and Resource Consumption](#chann)
* [Veeam Backup Job Name](#jname)

For more information about Veeam Backup & Replication backup jobs, see [Backup Job in Veeam Backup & Replication](rman_job_vbr.md).

Hosting Environments and Backup Job Names

By default, for standalone servers, Veeam Plug-In uses the Oracle server hostname to create the name for the Veeam Backup & Replication backup job and backup folder. In some cases, different standalone servers can have the same hostname in multiple environments. The procedure below describes how to differentiate between standalone server names.

Keep in mind that for servers in Oracle RAC environments, Veeam Backup & Replication generates the backup job name based on the single client access name (SCAN) of the cluster. For more information about backup job naming methods, see [Veeam Backup Job Name](#jname).

To identify standalone servers, update the Veeam configuration XML file as follows:

1. Open the Veeam configuration XML file. The path to the file differs depending on the OS of the machine where Veeam Plug-In is installed:

* On machines running Linux or Unix OS: /opt/veeam/VeeamPluginforOracleRMAN/veeam\_config.xml
* On machines running Windows OS: %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\veeam\_config.xml

1. Add one of the following parameters to the <PluginParameters /> line in the Veeam configuration XML file:

* The customServerName parameter:

|  |
| --- |
| <PluginParameters customServerName="<hostname.domain.tld>" /> |

where <hostname.domain.tld> is the custom name of the server.

After adding this parameter, Veeam Plug-In will use the specified custom name of the server to name the backup job and backup folder.

For example:

|  |
| --- |
| <PluginParameters customServerName="srv01.tech.local" /> |

* The useFQDNInServerName parameter:

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

1. Locate the Veeam configuration XML file. The path to the file differs depending on the OS of the machine where Veeam Plug-In is installed:

* On machines running Linux or Unix OS: /opt/veeam/VeeamPluginforOracleRMAN/veeam\_config.xml
* On machines running Windows OS: %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\veeam\_config.xml

1. Add the following parameter to the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters IgnoreVBRNetworkRules="true" /> |

For details on traffic encryption, see [Enabling Traffic Encryption](enable_network_encryption.md).

Veeam Backup Job Name

Consider the following:

* On the Veeam Backup & Replication server, the backup job name will be created automatically based on the server or cluster name and selected repository.
* For environments that use Oracle RMAN copy processing, one job per repository is created.

RMAN Channels and Resource Consumption

Any parallel channel started by RMAN will use one Veeam backup repository task slot. By design, Oracle Standard Edition can work with one channel. Oracle Enterprise Edition has the option to use multiple channels and you can configure them in the Veeam Plug-In configuration wizard or at the ALLOCATE CHANNEL definition in RMAN scripts. It is recommended to carefully plan repository task slots, so that Oracle RMAN can work with multiple channels in parallel when configured.

The following hardware resources are recommended based on tests on Skylake processors:

* Oracle server: 1 CPU core and a minimum of 200 MB of RAM per currently used channel. Note that resource consumption on the Oracle server depends on hardware and Oracle settings.
* Backup repository server: 1 CPU core and 1 GB of RAM per 5 currently used channels.

These resources are recommended only if you use a dedicated backup repository for Veeam Plug-In backups. If you use the same backup repository for Veeam Plug-In backups and backups created by Veeam Backup & Replication or Veeam Agents, consider adding the mentioned above hardware resources based on usual load on your backup repository. For details on hardware requirements for a backup repository, see [Backup Server System Requirements](system_requirements.md#repo).

We recommend to contact your Veeam system engineer to optimize the channel settings and resource allocation. Also, consider the following:

* It is recommended to use a separate backup repository for Veeam Plug-In backups.

* The control file does not use a repository task slot and will be processed even if there are no free task slots.

* Veeam Backup & Replication server: during manual metadata operations such as [import of backup files](import_backups_rman.md), the Veeam Backup & Replication server needs additional 15 GB of RAM per 1 million files located in the same backup job folder.



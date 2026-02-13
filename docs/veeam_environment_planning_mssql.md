---
title: "Veeam Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_environment_planning_mssql.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
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

Data Streams and Resource Consumption

Veeam Plug-In for Microsoft SQL Server transfers backup data from the machine with protected Microsoft SQL Server to Veeam backup repository using data streams. By default, Veeam Plug-In uses one data stream per backup operation. You can configure Veeam Plug-In to use additional data streams that will process backup data in parallel. This may be helpful if you want to reduce time spent on your backup operations.

If you want to use additional data streams, configure the Concurrent backup streams setting at the Backup Options step of the Back Up Database wizard. The Concurrent backup streams setting defines the maximum allowed number of data streams being used for each database. For details, see [Specify Backup Options](backup_job_options.md).

Hardware Resource Recommendations

Additional data streams increase load on the hardware of your infrastructure components. We recommend to carefully plan hardware resources, so that Microsoft SQL Server can work with multiple streams in parallel. The following hardware resources are recommended based on tests on Skylake processors:

* Microsoft SQL Server:

* 1 CPU core per 2 parallel backup streams.
* 1 GB of RAM per 5 parallel backup streams.

Besides resource recommendations, Veeam Plug-In may limit the number of data streams assigned to a certain database. For details, see [Data Stream Distribution on Microsoft SQL Server](#distr).

* Backup repository server. 1 CPU core and 1 GB of RAM per 5 parallel backup streams.

These resources are recommended only if you use a dedicated backup repository for Veeam Plug-In backups. If you use the same backup repository for Veeam Plug-In backups and VM backups created by Veeam Backup & Replication or Veeam Agents, consider adding the mentioned above hardware resources based on usual load on your backup repository. For details on hardware requirements for a backup repository, see [System Requirements](system_requirements.md#repo).

We recommend to contact your Veeam system engineer to optimize the backup stream settings and resource allocation. Also, note that it is recommended to use a separate backup repository for Veeam Plug-In backups.

* Veeam Backup & Replication server: during manual metadata operations such as [import of backup files](import_backups_rman.md), the Veeam Backup & Replication server needs additional 15 GB of RAM per 1 million files located in the same backup job folder.

Data Stream Distribution on Microsoft SQL Server

Veeam Plug-In for Microsoft SQL Server distributes data streams between databases that you want to back up in accordance to the resources available on Microsoft SQL Server and backup repository server. As a result, available data streams are distributed considering the following:

* Number of CPU cores on Microsoft SQL Server: Veeam Plug-In can assign no more than 2 data streams per 1 CPU core.
* Amount of RAM on Microsoft SQL Server: Veeam Plug-In can assign no more than 5 data streams per 1 GB RAM.

* Number of available task slots in the backup repository: each parallel data stream uses 1 task slot of the backup repository. To learn how to edit the number of concurrent tasks allowed for the backup repository, see the [Limitation of Concurrent Tasks](limiting_tasks.md#task-limitation-for-backup-repositories) section in Veeam Backup & Replication User Guide.

Example:

You want to back up 2 databases. Using the Concurrent backup streams setting, you set a maximum allowed number of data streams for each database as 5. Thus, you need 10 data streams to back up 2 databases with parallel data streams.

Your Microsoft SQL Server has 4 CPU cores and 4 GB RAM. Your backup repository has 10 available task slots. In this example, the number of data streams is limited by the CPU of your Microsoft SQL Server: 8 data streams in total.

As a result, Veeam Plug-In will split there data streams between 2 databases and process these databases in parallel: Veeam Plug-In will process the first database using 5 parallel streams and the second database using 3 parallel streams. Keep in mind, if number of available data streams is enough for 1 database only, Veeam Plug-In will process databases one by one.



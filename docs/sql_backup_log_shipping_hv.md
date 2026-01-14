---
title: "Log Shipping Servers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sql_backup_log_shipping_hv.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Log Shipping Servers

In this article

For every Microsoft SQL Server VM whose transaction logs you want to back up, Veeam Backup & Replication defines how to ship logs to the backup repository. Transaction logs can be shipped in the following ways:

* Direct connection. If it is possible to establish a direct connection between the VM guest OS and backup repository, log files will be shipped directly from the VM guest OS to the backup repository. This is the optimal method, as it does not involve additional resources and puts less load on the VM guest OS.
* Over log shipping server. If direct connection is not possible, files will be shipped through log shipping servers. A log shipping server is a Microsoft Windows server added to the backup infrastructure.

Note that if direct connection is possible, files will be always transferred from VM guest to repository directly (regardless of the configured log shipping server, as this server will not be involved). This approach helps to optimize performance at file transfer.

Data Transfer Methods

Log shipping servers can transfer data in two ways:

* Over the network. Veeam Backup & Replication obtains files from the VM guest OS and transfers them over the network. You can explicitly define what servers you want to use for log shipping or instruct Veeam Backup & Replication to automatically choose an optimal log shipping server. Veeam Backup & Replication chooses the log shipping server based on two criteria: possible data transfer methods and location of the Microsoft SQL Server VMs and log shipping server. For more information, see [Location of Log Shipping Server and VMs](#location).

To offload the VM guest OS, logs are created one by one (not simultaneously). One log creation request is issued for every DB.

* Over PowerShell Direct. Veeam Backup & Replication obtains transaction logs from the VM guest OS using PowerShell Direct, by communicating through the Hyper-V host. First, the logs are copied from the VM to a temporary folder on the Hyper-V host. Next, the logs are transferred from the host to the log shipping server and then to the backup repository. Veeam Backup & Replication  uses the backup server as the log shipping server, no matter which log shipping server is selected in the backup job settings.

PowerShell Direct is used for VMs that reside on Microsoft Hyper-V Server 2016 (or later) and run Microsoft Windows 10 (or later) or Microsoft Windows Server 2016 (or later). Veeam Backup & Replication requires Microsoft PowerShell 2.0 (or later) to work over PowerShell Direct.

The default method is log shipping over the network.

Location of Log Shipping Server and VMs

When choosing a log shipping server to transfer data over the network, Veeam Backup & Replication considers the location of the Microsoft SQL Server VM and log shipping server. Veeam Backup & Replication uses the following priority rules to select the log shipping server:

1. Log shipping server is located on the source Microsoft Hyper-V host performing the role of the on-host backup proxy.
2. Log shipping server and Microsoft SQL Server VM are located in the same network.
3. Log shipping server and Microsoft SQL Server VM are located in different networks (the production infrastructure is isolated from the backup infrastructure).

That is, when choosing a log shipping server, Veeam Backup & Replication will give the top priority to a Microsoft Windows VM that is located on the source Microsoft Hyper-V host.

Log shipping servers are assigned per job session. When a new job session starts, Veeam Backup & Replication detects log shipping servers anew. Veeam Backup & Replication can also re-detect available servers during the job session. If a log shipping server becomes unavailable for some reason, Veeam Backup & Replication will fail over to another log shipping server.

|  |
| --- |
| Important |
| If you do not want to use some servers for transaction logs transport, you can manually define what server Veeam Backup & Replication must use as a log shipping server in the job settings. It is recommended that you assign the log shipping server role to a number of servers for availability purposes. |

![Log Shipping Servers](images/log_shipping_sql_hv.webp)

Page updated 11/19/2025

Page content applies to build 13.0.1.1071

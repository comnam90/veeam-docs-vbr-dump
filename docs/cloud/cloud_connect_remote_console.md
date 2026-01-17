---
title: "Remote Access Console"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_remote_console.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Remote Access Console


The Remote Access Console is a Veeam Cloud Connect infrastructure component that provides access to the tenant backup server. With the Remote Access Console, the SP can connect to the tenant backup server, log on to Veeam Backup & Replication deployed on the tenant side and perform required data protection, disaster recovery or administration tasks.

The Remote Access Console is in many ways similar to the regular Veeam Backup & Replication console: it is a client-side component that communicates to the backup server. However, the Remote Access Console does not connect directly to the tenant backup server. Instead, it communicates to the Veeam Backup Service and Cloud network redirector running on the SP backup server. Veeam Backup & Replication passes commands from the Remote Access Console to the tenant backup server through network redirectors. To learn more, see [How Remote Access Console Works](cloud_connect_remote_console_hiw.md).

|  |
| --- |
| Note |
| For more information about the regular Veeam backup console, see the [Backup & Replication Console](https://helpcenter.veeam.com/docs/vbr/userguide/backup_console.html?ver=13) section in the Veeam Backup & Replication User Guide. |

The Remote Access Console is available on every machine where the regular Veeam backup console is installed. On the SP backup server, Veeam Backup & Replication creates a desktop icon for the Remote Access Console. On other machines where the Veeam backup console is installed, to open the Remote Access Console, use the following command:

|  |
| --- |
| "%ProgramFiles%\Veeam\Backup and Replication\Console\veeam.backup.shell.exe" -TenantRemoteAccess |

To connect to the tenant backup server, the SP needs to specify the following settings:

* The name or IP address of the SP backup server or cloud gateway (Depending on the location of the Remote Access Console. To learn more, see [Deployment Scenarios for Remote Access Console](cloud_connect_remote_console_deploy.md).)
* Credentials to connect to the SP backup server
* Credentials to connect to the tenant backup server

|  |
| --- |
| Note |
| The process of establishing a connection to the SP and tenant backup servers with the Remote Access Console may require longer time depending on the distance between these components and quality of the network connection. |

The SP can use the same Remote Access Console to connect to different tenant backup servers. For convenience, the SP can save several shortcuts for these connections.

Related Topics

* [Deployment Scenarios for Remote Access Console](cloud_connect_remote_console_deploy.md)
* [How Remote Access Console Works](cloud_connect_remote_console_hiw.md)
* [Limitations for Remote Access Console](cloud_connect_remote_limitations.md)

Related Tasks

[Using Remote Access Console](cc_remote.md)



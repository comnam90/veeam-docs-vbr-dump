---
title: "Remote Desktop Connection to Tenant"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_remote_desktop.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can use the Remote Access Console functionality to connect to the tenant backup server that runs the Microsoft Window OS over the Remote Desktop Protocol. In this case, the SP can log on to the Microsoft Windows OS on the tenant backup server and open the Veeam Backup & Replication console locally on this backup server. This may be required if the SP needs to perform operations that are not supported in the Remote Access Console, such as file-level or application items restore.

To connect to the tenant backup server, Veeam Backup & Replication uses the Remote Desktop Connection client (mstsc.exe). Veeam Backup & Replication opens the Remote Desktop Connection client locally on the machine where the Remote Access Console is installed. The Remote Desktop Connection client connects to Remote Desktop Services running on the tenant backup server. The connection is held over the communication channel opened between network redirectors. To learn more, see [How Remote Desktop Connection to Tenant Works](cloud_connect_remote_desktop_hiw.md).

The SP can launch a remote desktop session to the tenant backup server in one of the following ways:

* From the Cloud Connect view of the Veeam Backup & Replication console connected to the SP backup server. In this case, the SP can select the necessary tenant and their backup server in the Tenants node of the Cloud Connect view.
* From the Open Remote Access Console window on any machine where the Remote Access Console is installed. After the SP specifies settings to connect to the tenant backup server, they can press and hold the [CTRL] key and click Connect. Instead of connecting to the tenant backup server with the Remote Access Console, Veeam Backup & Replication will launch the Remote Desktop Connection client.
* If the SP and tenant run different versions of Veeam Backup & Replication on their backup servers, Veeam Backup & Replication will display a warning in the Open Remote Access Console window notifying that the Remote Access Console is unable to connect to the tenant backup server. In the warning, Veeam Backup & Replication will display a link to launch the Remote Desktop Connection client.

|  |
| --- |
| Note |
| You can also launch the Remote Desktop Connection client from the main menu of the Veeam Backup & Replication console. In this case, Veeam Backup & Replication will open a remote desktop session to the backup server to which the Veeam backup console is connected. |

Related Tasks

[Launching Remote Desktop Session to Tenant](cc_remote_desktop.md)

Page updated 11/3/2025

Page content applies to build 13.0.1.1071

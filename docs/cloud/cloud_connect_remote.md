---
title: "Remote Connection to Tenant Backup Server"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_remote.html"
last_updated: "9/17/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can use the Veeam Backup & Replication console to connect to the tenant backup server. This may be helpful, for example, if the tenant encounters a problem with managing its backup infrastructure and asks the SP to change settings in Veeam Backup & Replication deployed on the tenant side. The remote connection functionality allows the SP to manage tenant backup servers without the need to configure additional network connections, thus reducing security risks and network management overhead.

The remote connection functionality is available to the SP and tenant if the following conditions are met:

* The tenant connected to the SP using credentials of a standalone tenant account.

Remote connection to a backup server of a tenant with a VMware Cloud Director tenant account is not supported. To overcome this limitation, the SP can create a separate standalone account for this tenant, and the tenant can connect to the SP using credentials of this account.

* The tenant enabled the Allow this Veeam Backup & Replication installation to be managed by the service provider option at the process of connecting to the SP. To learn more, see [Specify Cloud Gateway Settings](cloud_connect_sp_settings.md).

Veeam Backup & Replication offers two types of connection to the tenant backup server:

* With the Remote Access Console — in this case, the SP can log on to the tenant backup server and perform the required operations in Veeam Backup & Replication. For example, the SP can use the Remote Access Console to change configuration options in Veeam Backup & Replication, run jobs or perform available restore tasks.
* With the Remote Desktop Connection client — in this case, the SP can launch a remote session over the RDP protocol and log on to the Microsoft Windows OS running on the tenant backup server.

To establish and keep remote connections between the tenant backup server and Veeam Cloud Connect infrastructure components on the SP side, Veeam Backup & Replication uses network redirectors. Network redirectors communicate through the cloud gateway allowing Veeam Backup & Replication components deployed on the SP side to access the tenant backup server. To learn more, see [Network Redirectors](cloud_connect_network_redirectors.md).

Related Topics

* [Network Redirectors](cloud_connect_network_redirectors.md)
* [Remote Access Console](cloud_connect_remote_console.md)
* [Remote Desktop Connection to Tenant](cloud_connect_remote_desktop.md)

Related Tasks

[Using Remote Access Console](cc_remote.md)

Page updated 9/17/2025

Page content applies to build 13.0.1.1071

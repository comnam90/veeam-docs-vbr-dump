---
title: "cloud_connect_remote_limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_remote_limitations.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---


In this article

The Remote Access Console has the following limitations:

* The Remote Access Console must be of exactly the same version as Veeam Backup & Replication installed on the tenant backup server.

In case versions differ, the Remote Access console will display a notification offering to establish a remote desktop connection to the tenant backup server. To learn more, see [Remote Desktop Connection to Tenant](cloud_connect_remote_desktop.md).

* The connection to the tenant backup server with the Remote Access Console is not supported if multi-factor authentication (MFA) is enabled for the user account in the Veeam Backup & Replication console on that backup server.

* The SP cannot perform the following operations with the Remote Access Console:

* Perform file-level restore
* Perform application items restore with Veeam Explorers
* Perform file copy operations using the Files view of the Veeam Backup & Replication console

To overcome this limitation, the SP can establish a remote desktop connection to the tenant backup server. After that, the SP can perform necessary operations in the Veeam Backup & Replication console deployed locally on the tenant backup server.

Page updated 11/3/2025

Page content applies to build 13.0.1.1071

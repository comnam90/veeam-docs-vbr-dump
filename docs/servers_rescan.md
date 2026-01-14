---
title: "Rescanning Servers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/servers_rescan.html"
last_updated: "5/31/2023"
product_version: "13.0.1.1071"
---

# Rescanning Servers

In this article

In some cases, you may need to rescan hosts or servers in the backup infrastructure. The rescan operation may be required if you have added or removed new disks and volumes to/from the host or server and want to display actual information in Veeam Backup & Replication. During the rescan operation, Veeam Backup & Replication retrieves information about disks and volumes that are currently connected to a host or server and stores this information to the configuration database.

Veeam Backup & Replication automatically performs a rescan operation every 4 hours. You can also start the rescan operation manually:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Managed servers.
3. In the working area, select the server or host and click Rescan on the ribbon. Alternatively, you can right-click the server or host and select Rescan.

[![Click to zoom in](images/servers_rescan.webp)](images/servers_rescan.webp "Click to zoom in")

Page updated 5/31/2023

Page content applies to build 13.0.1.1071

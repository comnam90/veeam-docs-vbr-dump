---
title: "Viewing Snapshots and Backups"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/view_backups.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

In the Veeam Backup & Replication console, you can view information about snapshots and backups exported by Veeam Kasten policies or manually. Veeam Backup & Replication displays the backups and snapshots located in both Veeam backup repositories and other location profiles, such as object storage repositories.

Available backups and snapshots are displayed in the Home view:

* The Backups node shows exports created by Veeam Kasten policies.
* The Snapshots subnode shows snapshots created by Veeam Kasten policies.

When you expand a node in the working area, you can see the following icons:

| Icon | State |
| --- | --- |
| ![Viewing Snapshots and Backups](images/icon_full.webp) | Kasten snapshot or export |
| ![Viewing Snapshots and Backups](images/k10_application.webp) | Kasten application |

This information in the working area provides the following data:

* Veeam backup repository and folder on this repository where the backup is stored.
* Available restore points.
* Date of restore points creation.
* Data size and backup file size.
* A type of platform service where backups are created.

Page updated 8/26/2024

Page content applies to build 13.0.1.1071

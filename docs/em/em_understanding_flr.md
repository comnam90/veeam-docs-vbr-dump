---
title: "File-Level Restore Capabilities"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_understanding_flr.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---


In this article

When you restore files from the restore point created for a virtual or physical machine with guest OS file indexing enabled, Veeam uses the following workflow:

1. To provide for browsing and search, Veeam uses index data to represent the file system of the guest OS.
2. If you then select to download the necessary files, Veeam Backup & Replication will mount virtual or physical machine disks (from the restore point in repository) on the Veeam backup server and then copy these files from the backup server to the target location.
3. If you select to restore files to the original location, an additional mount point will be created on the mount server associated with the backup repository storing the backup file. During restore, machine data will flow from repository to target, keeping the machine traffic in one site and reducing load on the network.
4. After you download or restore the necessary files, and finish the restore session, the machine (or server) disks will be unmounted.

When you restore files from the restore point that was created without guest OS file indexing, Veeam Backup & Replication uses the following workflow:

1. To provide for browsing, disks of the virtual machine or physical server from the backup file are mounted to the backup server.
2. If you then select to download the necessary files, Veeam Backup & Replication will copy these files from the backup server to the destination location, using this mount point.
3. If you select to restore files from the backup to the original location on the production machine, an additional mount point will be created on the mount server associated with the backup repository storing the backup file.
4. If you restore machine files from a VM replica, a single mount point for all these operations (browsing, download, restore to original location) will be created on the backup server.
5. After you download or restore the necessary files, and finish the restore session, the machine (or server) disks will be unmounted.

Page updated 12/10/2024

Page content applies to build 13.0.1.1071

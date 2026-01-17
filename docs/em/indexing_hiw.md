---
title: "How Indexing Works"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/indexing_hiw.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---


In this article

When you run a backup job with the file indexing option enabled, Veeam Backup & Replication indexes the machine file system, collects indexing data and writes it to the GuestIndexData.zip file. The GuestIndexData.zip file is first stored in a temporary folder on the backup server.

As soon as the backup job completes, Veeam Backup & Replication notifies the local Veeam Backup Catalog service. The service saves indexing data in the Veeam Backup Catalog folder on the backup server. During the next catalog replication session started on Veeam Backup Enterprise Manager, indexing data from the backup server is replicated to the Veeam Backup Catalog on Veeam Backup Enterprise Manager server. By federating indexing data from all connected backup servers, the Veeam Backup Catalog service on Veeam Backup Enterprise Manager creates a global catalog for the whole backup infrastructure.

Veeam Backup & Replication supports file-level restore not only for machines included in guest catalog but also for the machines that are not indexed. Indexing may be disabled at the time of restore point creation, or indexing operation may fail. In this case, the restore point of a Windows machine is mounted to the backup server that manages the job, and the restore point of a non-Windows machine is mounted to a helper host or helper appliance.

Then a user will be able to locate the necessary files and folders and perform restore operation. For more information, see [Guest OS File Restore](searching_restoring_vm_guest_files.md).

Page updated 12/10/2024

Page content applies to build 13.0.1.1071

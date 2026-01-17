---
title: "Data Restore from Deleted Backups"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_bin_restore.html"
last_updated: "1/26/2024"
product_version: "13.0.1.1071"
---


In this article

In contrast to backups that reside on the cloud repository, backup files in the "recycle bin" are not intended for regular data restore. However, in a situation where an attacker manages to delete tenant backups from a cloud repository, or if the tenant deletes a backup from a cloud repository by mistake, the tenant may need to restore data from a backup file that was moved to the "recycle bin". Data restore directly from a backup file in the "recycle bin" is not supported in Veeam Backup & Replication. To restore data from such a backup, the tenant needs to obtain backup files from the "recycle bin" first.

Veeam Backup & Replication moves to the "recycle bin" only backup files of the VBK and VIB type. VBM files are deleted from disk immediately when a tenant deletes a backup or a backup file is automatically deleted from the backup chain according to the retention policy. As a result, the SP cannot simply move a backup file back to the folder with tenant backups on the cloud repository. Instead, the SP and tenant need to complete the following steps:

1. The tenant contacts the SP informing that they want to restore data from a deleted backup.

|  |
| --- |
| Important |
| Before restoring data from a deleted backup, the tenant must make sure that a VBM file with metadata of this backup does not remain on the cloud repository. If a tenant needs to restore data from a deleted backup file pertaining to a backup that still exists on the cloud repository, the tenant must delete this backup prior to importing a VBK file in the tenant backup console.  For assistance with data restore from a deleted backup, consider submitting a support case to the [Veeam Customer Support](https://www.veeam.com/support.html). |

1. The SP finds one or more backup files required for data restore in the "recycle bin" and passes them to the tenant, for example, over the network or on a portable drive.

Alternatively, if the SP uses a simple backup repository as a cloud repository, the SP can copy backup files from the "recycle bin" to the folder with tenant backups in the cloud repository. The tenant can then copy the backup files from the cloud repository using the Files view in the tenant Veeam Backup & Replication console.

|  |
| --- |
| Note |
| If the SP uses the capacity tier functionality, and deleted backups reside in capacity tier, the SP must locate the necessary backup files and download them from capacity tier using Windows PowerShell scripts. For details, contact [Veeam Customer Support](https://www.veeam.com/support.html). |

1. The tenant imports the VBK files in the Veeam Backup & Replication console on the tenant backup server.
2. After successful import of a backup, the tenant can restore data from the backup in a regular way.
3. [Optional] The tenant may want to continue the backup chain started with the obtained backup files. This operation can be available depending on multiple conditions. For details, consider submitting a support case to the [Veeam Customer Support](https://www.veeam.com/support.html).

Page updated 1/26/2024

Page content applies to build 13.0.1.1071

---
title: "cc_archive_tier_publish"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_archive_tier_publish.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can retrieve tenant data from the archive tier. This operation is required if the tenant needs to restore data from a restore point that was offloaded to the archive tier: it is not possible to restore data from such restore points immediately. To perform the retrieve operation, the SP must use Veeam PowerShell cmdlets.

To retrieve the tenant data, follow these steps:

1. Obtain the restore point ID from the tenant.

If the tenant is unsure which restore point to use, or if you manage the tenant Veeam Backup & Replication environment, ask the tenant to provide you with information about the point in time to which the tenant wants to restore data. Then, you can use the Get-VBRCloudArchiveRestorePoint PowerShell cmdlet to get a list of restore points located in the archive tier and obtain the restore point ID. For detailed instructions, see the [Get-VBRCloudArchiveRestorePoint](https://helpcenter.veeam.com/docs/backup/powershell/get-vbrcloudarchiverestorepoint.html) section in the Veeam PowerShell Reference.

1. Run the Publish-VBRCloudArchiveRestorePoint PowerShell cmdlet. This cmdlet retrieves tenant data from archive storage and places them in the capacity tier of the scale-out backup repository.

Use the restore point ID as a parameter value when performing the operation. For detailed instructions, see the [Publish-VBRCloudArchiveRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/publish-vbrcloudarchiverestorepoint.html?ver=13) section in the Veeam PowerShell Reference.

1. After the data is retrieved, notify the tenant that the data is ready. The tenant can then restore the data from the specified restore point.

Page updated 11/19/2025

Page content applies to build 13.0.1.1071

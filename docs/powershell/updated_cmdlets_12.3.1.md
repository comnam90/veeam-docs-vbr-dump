---
title: "Updated Cmdlets"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/updated_cmdlets_12.3.1.html"
last_updated: "6/11/2025"
product_version: "13.0.1.1071"
---

# Updated Cmdlets


This section contains information on cmdlets updated in Veeam PowerShell v12.3.1.

Backup Infrastructure

Object Storage Repositories

In this version, you can use new parameter set to add Veeam Data Cloud Vault using a subscription.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRDataCloudVaultRepository](add-vbrdatacloudvaultrepository.md) | New parameter set added: Add-VBRDataCloudVaultRepository [-Name <String>] [-Description <String>] [-Vault <VBRVeeamDataCloudAssignedVault>] [-Folder <String>] [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-ForceOwnershipChange] [-Force] [<CommonParameters>] | |

Backup

Managing Backups

In this version, Cloud Connect backups are removed when using the FromDisk parameter of the Remove-VBRBackup cmdlet.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Remove-VBRBackup](remove-vbrbackup.md) | Parameter Updated: FromDisk parameter also removes Cloud Connect backups. | |



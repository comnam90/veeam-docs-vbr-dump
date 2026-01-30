---
title: "Updated Cmdlets"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/updated_cmdlets_v13.0.1.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Updated Cmdlets


This section contains information on cmdlets updated in Veeam PowerShell v13.0.1.

Backup Infrastructure

WAN Acceleration

In this version, you can use the Force parameter to create a new WAN accelerator without showing warnings in the PowerShell console.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRWANAccelerator](add-vbrwanaccelerator.md) | New parameter: Force. | |

Backup

Working with Jobs

In this version, you can use new parameters to specify the encryption keys and KMS servers.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRHvBackupJob](add-vbrhvbackupjob.md) | New parameters: EncryptionKey, KMSServer. | | [Add-VBRvCloudJob](add-vbrvcloudjob.md) | New parameters: EncryptionKey, KMSServer. | | [Add-VBRViBackupJob](add-vbrvibackupjob.md) | New parameters: EncryptionKey, KMSServer. | |

Veeam Agent Management

Veeam Agent Management Protection Groups

In this version, you can use the InstallCDPAgent parameter to install the Veeam CDP Agent Service and Veeam CDP Volume Filter Driver.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRProtectionGroupDeploymentOptions](new-vbrprotectiongroupdeploymentoptions.md) | New parameter: InstallCDPAgent. | |

Veeam Plug-Ins for Enterprise Applications

Application Backup Policies

In this version, you can use new parameters to specify the backup settings, storage settings and credentials for Veeam Plug-In for Microsoft SQL Server.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRApplicationBackupJob](add-vbrapplicationbackupjob.md) | New parameters: MSSQLStorageOptions, MSSQLOptions, MSSQLCredentialsOptions. | | [Set-VBRApplicationBackupJob](set-vbrapplicationbackupjob.md) | New parameters: MSSQLStorageOptions, MSSQLOptions, MSSQLCredentialsOptions. | |

Application Backup Policy Database Processing

In this version, you can use the MSSQLProcessingOptions parameter to specify the Microsoft SQL Server database processing settings.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md) | New parameter: MSSQLProcessingOptions. | | [Set-VBRDatabaseProcessingOptions](set-vbrdatabaseprocessingoptions.md) | New parameter: MSSQLProcessingOptions. | |

Veeam Cloud Connect

Managing Backups

In this version, you can use All parameter to get all types of backups for the tenant account.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRCloudTenantBackup](get-vbrcloudtenantbackup.md) | New parameter: All. | |



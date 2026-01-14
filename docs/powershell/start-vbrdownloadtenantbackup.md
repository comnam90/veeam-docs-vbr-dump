---
title: "Start-VBRDownloadTenantBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrdownloadtenantbackup.html"
last_updated: "3/25/2024"
product_version: "13.0.1.1071"
---

# Start-VBRDownloadTenantBackup

In this article

Short Description

Downloads tenant backups from capacity tier to performance tier.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRDownloadTenantBackup -CloudTenant <IVBRCloudTenant[]> [-FullBackupChain]  [<CommonParameters>] |

Detailed Description

This cmdlet downloads tenant backups from capacity tier to performance tier.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies an array of cloud tenants. The cmdlet will download tenant backups from capacity tier to performance tier. | Accepts the IVBRCloudTenant[] object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| FullBackupChain | Defines that the cmdlet will download tenant backup files from both active and inactive backup chain.  If you do not specify this parameter, the cmdlet will download only tenant backups that belong to an active backup chain. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Downloading Tenant Backup Files

|  |  |
| --- | --- |
| This example shows how to download the ABC Company tenant backup files.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  Start-VBRDownloadTenantBackup -CloudTenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the Start-VBRDownloadTenantBackup cmdlet. Set the $tenant variable as the CloudTenant parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Downloading all Tenant Backup Files

|  |  |
| --- | --- |
| This example shows how to download the ABC Company tenant backup files from both active and inactive backup chains.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  Start-VBRDownloadTenantBackup -CloudTenant $tenant -FullBackupChain |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the Start-VBRDownloadTenantBackup cmdlet. Set the $tenant variable as the CloudTenant parameter value. Provide the FullBackupChain parameter. |

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)

Page updated 3/25/2024

Page content applies to build 13.0.1.1071

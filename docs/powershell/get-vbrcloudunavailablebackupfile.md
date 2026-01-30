---
title: "Get-VBRCloudUnavailableBackupFile"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudunavailablebackupfile.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudUnavailableBackupFile


Short Description

Returns a list of backup files that are no longer available in the cloud repository.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCloudUnavailableBackupFile -CloudTenant <IVBRCloudTenant>  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of backup files that are no longer available in the cloud repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies a cloud tenant account for which you want to get backup files that are no longer available in the cloud repository. | Accepts the IVBRCloudTenant object. To create this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudUnavailableBackupFile](vbrcloudunavailablebackupfile.md)

Examples

Getting Unavailable Backup Files for Cloud Tenant Account

This example shows how to get a list of backup files that are no longer available in the cloud repository for the ABC Company cloud tenant account.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  $backupfiles = Get-VBRCloudUnavailableBackupFile -CloudTenant $tenant |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the Get-VBRCloudUnavailableBackupFile cmdlet. Set the $tenant variable as the CloudTenant parameter value. Save the result to the $backupfiles variable.

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)



---
title: "Add-VBRAzureExternalRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazureexternalrepository.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAzureExternalRepository

In this article

Short Description

Adds external Microsoft Azure Blob storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureExternalRepository -AzureBlobFolder <VBRAzureBlobFolder> -Connection <VBRAzureBlobConnection> [-Name <string>] [-Description <string>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-DecryptBackups] [-DecryptionKey <VBREncryptionKey>] [-Force] [-AzureSubscription <VBRAzureSubscription>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds external Microsoft Azure Blob storage repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AzureBlobFolder | Specifies a name of an Azure Blob storage container where Azure VMs backups reside. | Accepts the VBRAzureBlobFolder object. To get this object, run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with Microsoft Azure Blob storage that you want to add as an external repository. | Accepts the VBRAzureBlobConnection object. To get this object, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet and set the ExternalRepository property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies a name of Microsoft Azure Blob storage that you want to add as an external repository. | String | False | Named | False |
| Description | Specifies a description of Microsoft Azure Blob storage that you want to add as an external repository. | String | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| DecryptBackups | Defines that Veeam Backup & Replication will decrypt encrypted backups.  Default: False. | SwitchParameter | False | Named | False |
| DecryptionKey | Specifies the password that Veeam Backup & Replication will use to decrypt the backup files. | Accepts the VBREncryptionKey object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add an external repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| AzureSubscription | Specifies subscriptions associated with a Microsoft Azure account. | Accepts the VBRAzureSubscription object. To get this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRAzureExternalRepository object that contains settings of Microsoft Azure Blob repositories added to the backup infrastructure.

Examples

Adding Microsoft Azure Blob Storage as External Repository

This example shows how to add the Microsoft Azure Blob storage as an external repository to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount  $connection = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType ExternalRepository  $container = Get-VBRAzureBlobContainer -Connection $connection -Name "Azure External Repository"  $folder = Get-VBRAzureBlobFolder -Container $container -Connection $connection  Add-VBRAzureExternalRepository -Name "AzureExternalRepo" -Description "New external repository" -AzureBlobFolder $folder -Connection $connection |

Perform the following steps:

1. Get the Azure Blob folder:

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Save the result to the $account variable.
2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable.
3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Set the $connection variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $container variable.
4. Run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. Set the $container variable as the Container parameter value. Set the $connection variable as the Connection parameter value. Save the result to the $folder variable.

1. Run the Add-VBRAzureExternalRepository cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Specify the Description parameter value.
* Set the $folder variable as the AzureBlobFolder parameter value.
* Set the $connection variable as the Connection parameter value.

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)
* [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md)
* [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md)

Page updated 7/23/2025

Page content applies to build 13.0.1.1071

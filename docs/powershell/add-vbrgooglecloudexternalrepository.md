---
title: "Add-VBRGoogleCloudExternalRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrgooglecloudexternalrepository.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---

# Add-VBRGoogleCloudExternalRepository


Short Description

Adds external Google Cloud storage repository to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRGoogleCloudExternalRepository -GoogleCloudFolder <VBRGoogleCloudFolder> -Connection <VBRGoogleCloudExternalConnection> [-Name <string>] [-Description <string>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-DecryptBackups] [-DecryptionKey <VBREncryptionKey>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds external Google Cloud storage repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| GoogleCloudFolder | Specifies the name of a folder in the external repository. Veeam Backup & Replication will import backups from this folder into the backup infrastructure. | Accepts the VBRGoogleCloudFolder object. To create this object, run the [Get-VBRGoogleCloudFolder](get-vbrgooglecloudfolder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies the active session with the Google Cloud storage that you want to add as an external repository. | Accepts the VBRGoogleCloudExternalConnection object. To get this object, run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet and set the ExternalRepository property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies the name of the Google Cloud storage that you want to add as an external repository. | String | False | Named | False |
| Description | Specifies the description of the Google Cloud storage that you want to add as an external repository. | String | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| DecryptBackups | Defines that Veeam Backup & Replication will decrypt encrypted backups.  Default: False. | SwitchParameter | False | Named | False |
| DecryptionKey | Specifies the password that Veeam Backup & Replication will use to decrypt the backup files. | Accepts the VBREncryptionKey object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add an external repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudExternalRepository object that contains settings of external Google Cloud storage repository.

Examples

Adding External Google Cloud Storage

This example shows how to add the Google\_Repository Google Cloud storage as an external repository to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -AccessKey "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"  $connection = Connect-VBRGoogleCloudService -Account $account  $bucket = Get-VBRGoogleCloudBucket -Connection $connection -Region $region  $folder = Get-VBRGoogleCloudFolder -Connection $connection -Bucket $bucket  Add-VBRGoogleCloudExternalRepository -GoogleCloudFolder $folder -Connection $connection -Name "Google\_Repository" |

Perform the following steps:

1. Get the Google Cloud folder:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $connection variable.
3. Run the [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md) cmdlet. Set the $connection variable as the Connection parameter value. Set the $region variable as the Region parameter value. Save the result to the $bucket variable.
4. Run the [Get-VBRGoogleCloudFolder](get-vbrgooglecloudfolder.md) cmdlet. Set the $connection variable as the Connection parameter value. Set the $bucket variable as the Bucket parameter value. Save the result to the $folder variable.

1. Run the Add-VBRGoogleCloudExternalRepository cmdlet. Set the $folder variable as the GoogleCloudFolder parameter value. Set the $connection variable as the Connection parameter value. Specify the Name parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)
* [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md)
* [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md)
* [Get-VBRGoogleCloudFolder](get-vbrgooglecloudfolder.md)



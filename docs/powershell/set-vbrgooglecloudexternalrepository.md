---
title: "Set-VBRGoogleCloudExternalRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrgooglecloudexternalrepository.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---

# Set-VBRGoogleCloudExternalRepository

In this article

Short Description

Modifies external Google Cloud storage repository.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGoogleCloudExternalRepository -ExternalRepository <VBRGoogleCloudExternalRepository> [-Name <string>] [-Description <string>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-DecryptBackups] [-DecryptionKey <VBREncryptionKey>] [-GatewayServer <CHost>]  [<CommonParameters>] |

Detailed Description

This cmdllet modifies external Google Cloud storage repository added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ExternalRepository | Specifies the external Google Cloud storage repository that you want to modify. | Accepts the VBRGoogleCloudExternalRepository object. To create this object, run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies the name of the Google Cloud storage repository. | String | False | Named | False |
| Description | Specifies the description of the Google Cloud storage. | String | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| DecryptBackups | Defines that Veeam Backup & Replication will decrypt encrypted backups.  Default: False. | SwitchParameter | False | Named | False |
| DecryptionKey | Specifies the password that Veeam Backup & Replication will use to decrypt the backup files. | Accepts the VBREncryptionKey object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| GatewayServer | Specifies the gateway server. Veeam Backup & Replication will use this server to access a Google Cloud bucket. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudExternalRepository object that contains settings of external Google Cloud storage repository added to the backup infrastructure..

Examples

Modifying Decryption Password of External Google Cloud Storage

This example shows how to modify the decryption password for the Google\_Repository external Google Cloud storage.

|  |
| --- |
| $repository = Get-VBRExternalRepository -Name "Google\_Repository"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $key = Add-VBREncryptionKey -Password $securepassword  Set-VBRGoogleCloudExternalRepository -ExternalRepository $repository -DecryptBackups -DecryptionKey $key |

Perform the following steps:

1. Run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6) cmdlet. Specify the message which the console will display as a prompt. Provide the AsSecureString parameter. Save the result to the $securepassword variable.
3. Run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. Set the $securepassword variable as the Password parameter value. Save the result to the $key variable.
4. Run the Set-VBRGoogleCloudExternalRepository cmdlet. Specify the following settings:

* Set the $repository variable as the ExternalRepository parameter value.
* Provide the DecryptBackups parameter.
* Set the $key variable as the DecryptionKey parameter value.

Related Commands

* [Get-VBRExternalRepository](get-vbrexternalrepository.md)
* [Add-VBREncryptionKey](add-vbrencryptionkey.md)

Page updated 7/23/2025

Page content applies to build 13.0.1.1071

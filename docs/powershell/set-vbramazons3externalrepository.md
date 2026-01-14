---
title: "Set-VBRAmazonS3ExternalRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbramazons3externalrepository.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---

# Set-VBRAmazonS3ExternalRepository

In this article

Short Description

Modifies external Amazon S3 storage repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAmazonS3ExternalRepository -ExternalRepository <VBRAmazonS3ExternalRepository> [-Name <string>] [-Description <string>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-DecryptBackups] [-DecryptionKey <VBREncryptionKey>] [-GatewayServer <CHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies external Amazon S3 storage repository added to the backup infrastructure.

|  |
| --- |
| Note |
| Consider the following:   * This cmdlet requires the PSCredential object. Use the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet to get the PSCredentials object. * To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ExternalRepository | Specifies the external Amazon S3 repository that you want to modify. | Accepts the VBRAmazonS3ExternalRepository object. To get this object, run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies the name of external Amazon S3 storage repository. | String | False | Named | False |
| Description | Specifies the description of external Amazon S3 storage repository. | String | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| DecryptBackups | Defines that Veeam Backup & Replication will decrypt encrypted backups.  Default: False. | SwitchParameter | False | Named | False |
| DecryptionKey | Specifies the password that Veeam Backup & Replication will use to decrypt the backup files.  Default: False. | Accepts the VBREncryptionKey object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| GatewayServer | Specifies the gateway server. Veeam Backup & Replication will use this server to access an Amazon S3 bucket. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonS3ExternalRepository object that contains settings of the modified external Amazon S3 storage repository added to the backup infrastructure..

Examples

Modifying Decryption Password of External Amazon S3 Storage Repository

This example shows how to modify the decryption password for external Amazon S3 storage repository.

|  |
| --- |
| $repository = Get-VBRExternalRepository -Name "External Repository"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $key = Add-VBREncryptionKey -Password $securepassword  Set-VBRAmazonS3ExternalRepository -ExternalRepository $repository -DecryptBackups -DecryptionKey $key |

Perform the following steps:

1. Run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6) cmdlet. Specify the message which the console will display as a prompt. Provide the AsSecureString parameter. Save the result to the $securepassword variable.
3. Run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. Set the $securepassword variable as the Password parameter value. Save the result to the $key variable.
4. Run the Set-VBRAmazonS3ExternalRepository cmdlet. Specify the following settings:

* Set the $repository variable as the ExternalRepository parameter value.
* Provide the DecryptBackups parameter.
* Set the $key variable as the DecryptionKey parameter value.

Related Commands

* [Get-VBRExternalRepository](get-vbrexternalrepository.md)
* [Add-VBREncryptionKey](add-vbrencryptionkey.md)

Page updated 7/23/2025

Page content applies to build 13.0.1.1071

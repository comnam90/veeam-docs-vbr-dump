---
title: "Set-VBRAzureExternalRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazureexternalrepository.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRAzureExternalRepository


Short Description

Modifies external Microsoft Azure Blob storage repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureExternalRepository -ExternalRepository <VBRAzureExternalRepository> [-Name <string>] [-Description <string>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-DecryptBackups] [-DecryptionKey <VBREncryptionKey>] [-GatewayServer <CHost>] [-AzureSubscription <VBRAzureSubscription>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies external Microsoft Azure Blob storage repository added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ExternalRepository | Specifies the Microsoft Azure Blob storage repository added as an external repository. The cmdlet will modify this repository. | Accepts the VBRAzureExternalRepository object. To get this object, run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies the name of Microsoft Azure Blob storage repository that you want to add as an external repository. | String | False | Named | False |
| Description | Specifies the description of Microsoft Azure Blob storage repository that you want to add as an external repository. | String | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| DecryptBackups | Defines that Veeam Backup & Replication will decrypt encrypted backups.  Default: False. | SwitchParameter | False | Named | False |
| DecryptionKey | Specifies the password that Veeam Backup & Replication will use to decrypt the backup files. | Accepts the VBREncryptionKey object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| GatewayServer | Specifies the gateway server. Veeam Backup & Replication will use this server to access Microsoft Azure Blob storage repository. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| AzureSubscription | Specifies the subscriptions associated with a Microsoft Azure account. | Accepts the VBRAzureSubscription object. To get this object, run the  [Get- VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRAzureExternalRepository object that contains settings of Microsoft Azure Blob storage repository added as an external repository.

Examples

Modifying Decryption Password of External Azure Blob Storage Repository

This example shows how to modify the decryption password of Microsoft Azure Blob storage repository named Microsoft Azure Repository.

|  |
| --- |
| $repository = Get-VBRExternalRepository -Name "Microsoft Azure Repository"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $key = Add-VBREncryptionKey -Password $securepassword  Set-VBRAzureExternalRepository -ExternalRepository $repository -DecryptBackups -DecryptionKey $key |

Perform the following steps:

1. Run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Specify the password to decrypt backup files:

* Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable.
* Run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. Set the $securepassword variable as the Password parameter value. Save the result to the $key variable.

1. Run the Set-VBRAzureExternalRepository cmdlet. Specify the following settings:

* Set the $repository variable as the ExternalRepository parameter value.
* Provide the DecryptBackups parameter.
* Set the $key variable as the DecryptionKey parameter value.

Related Commands

* [Get-VBRExternalRepository](get-vbrexternalrepository.md)
* [Add-VBREncryptionKey](add-vbrencryptionkey.md)



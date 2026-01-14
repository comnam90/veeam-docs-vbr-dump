---
title: "Add-VBRAmazonS3ExternalRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbramazons3externalrepository.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAmazonS3ExternalRepository

In this article

Short Description

Adds external Amazon S3 storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAmazonS3ExternalRepository -AmazonS3Folder <VBRAmazonS3Folder> -Connection <VBRAmazonS3ExternalConnection> [-Name <string>] [-Description <string>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-DecryptBackups] [-DecryptionKey <VBREncryptionKey>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds external Amazon S3 object storage repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| AmazonS3Folder | Specifies the name of a folder in the Amazon S3 bucket where EC2 instance backups reside. | Accepts the [VBRAmazonS3Folder](vbramazons3folder.md) object. To create this object, run the [New-VBRAmazonS3Folder](new-vbramazons3folder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies the active session with the Amazon S3 storage repository that you want to add as an external repository. | Accepts the VBRAmazonS3ExternalConnection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet and set the ExternalRepository property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies the name of the Amazon S3 storage repository that you want to add as an external repository. | String | False | Named | False |
| Description | Specifies the description of the Amazon S3 storage repository that you want to add as an external repository. | String | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| DecryptBackups | Defines that Veeam Backup & Replication will decrypt encrypted backups.  Default: False. | SwitchParameter | False | Named | False |
| DecryptionKey | Specifies the password that Veeam Backup & Replication will use to decrypt the backup files. | Accepts the VBREncryptionKey object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add an external repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonS3ExternalRepository object that contains settings of Amazon S3 repositories added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Amazon S3 External Repository

|  |  |
| --- | --- |
| This example shows how to add the Amazon S3 object storage repository named New Repository as an external repository into the backup infrastructure.    |  | | --- | | $account = Get-VBRAmazonAccount  $connect = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType ExternalRepository  $bucket = Get-VBRAmazonS3Bucket -Connection $connect -Name "veeam-tw"  $folder = Get-VBRAmazonS3Folder -Name "frozenbucket" -Bucket $bucket -Connection $connect  Add-VBRAmazonS3ExternalRepository -Name "New Repository" -AmazonS3Folder $folder -Connection $connect |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connect variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $bucket variable. 4. Run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. Specify the Name parameter value. Set the $bucket variable as the Bucket parameter value. Set the $connect variable as the Connection parameter value. Save the result to the $folder variable. 5. Run the Add-VBRAmazonS3ExternalRepository cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $folder variable as the AmazonS3Folder parameter value. * Set the $connect variable as the Connection parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Amazon S3 External Repository and Decrypting the Imported Backup Files

|  |  |
| --- | --- |
| This example shows how to add Amazon S3 object storage repository named New Repository as an external repository into the backup infrastructure. Veeam Backup & Replication will decrypt backup files that are imported from the external repository.    |  | | --- | | $account = Get-VBRAmazonAccount  $connect = Connect-VBRAmazonS3Service -Account $account[1] -RegionType Global -ServiceType ExternalRepository  $bucket = Get-VBRAmazonS3Bucket -Connection $connect -Name "veeam-tw"  $folder = Get-VBRAmazonS3Folder -Name "frozenbucket" -Bucket $bucket -Connection $connect  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $key = Add-VBREncryptionKey -Password $securepassword  Add-VBRAmazonS3ExternalRepository -Name "New Repository" -AmazonS3Folder $folder -Connection $connect -DecryptBackups -DecryptionKey $key |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Specify the Account, RegionType and ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connect variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $bucket variable. 4. Run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. Specify the Name parameter value. Set the $bucket variable as the Bucket parameter value. Set the $connect variable as the Connection parameter value. Save the result to the $folder variable. 5. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6) cmdlet. Specify the message which the console will display as a prompt. Specify the AsSecureString parameter. Save the result to the $securepassword variable. 6. Run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. Specify the Password parameter. Save the result to the $key variable. 7. Run the Add-VBRAmazonS3ExternalRepository cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $folder variable as the AmazonS3Folder parameter value. * Set the $connect variable as the Connection parameter value. * Provide the DecryptBackups parameter. * Set the $key variable as the DecryptionKey parameter value. |

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)
* [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md)
* [Get-VBRAmazonS3Folder](get-vbramazons3folder.md)
* [Add-VBREncryptionKey](add-vbrencryptionkey.md)

Page updated 7/23/2025

Page content applies to build 13.0.1.1071

---
title: "Add-VBRS3GlacierCompatibleRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrs3glaciercompatiblerepository.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VBRS3GlacierCompatibleRepository


Short Description

Adds S3 compatible object storage with data archiving to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRS3GlacierCompatibleRepository -AmazonS3Folder <VBRAmazonS3Folder> -Connection <VBRAmazonS3CompatibleConnection> [-Name <string>] [-Description <string>] [-EnableBackupImmutability] [-ArchiverAppliance <CHost>] [-ForceOwnershipChange] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdet adds S3 compatible object storage with data archiving to the backup infrastructure.

|  |
| --- |
| Important |
| To be able to work with S3 compatible object storage with data archiving, you must enable the SOSAPI functionality. For more information, see [Working with Veeam Smart Object Storage API (SOSAPI)](https://helpcenter.veeam.com/docs/vbr/userguide/sosapi.html?ver=13) section in Veeam Backup & Replication User Guide. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| AmazonS3Folder | Specifies a folder for S3 compatible object storage with data archiving. Veeam Backup & Replication will move backup files into this folder. | Accepts the VBRAmazonS3Folder object. To create this object, run the [New-VBRAmazonS3Folder](new-vbramazons3folder.md) cmdlet. To get this object, run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with S3 compatible object storage that supports data archiving. The cmdlet use it to add S3 compatible object storage as a backup repository. | Accepts the VBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3CompatibleService](connect-vbramazons3compatibleservice.md) cmdlet and set the ArchiveTier property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies a name of S3 compatible object storage with data archiving. The cmdlet will add S3 compatible object storage with this name. | String | False | Named | False |
| Description | Specifies a description of S3 compatible object storage with data archiving. The cmdlet will add S3 compatible object storage with this description. | String | False | Named | False |
| EnableBackupImmutability | Enables immutability for S3 compatible object storage with data archiving.  Default: False. | SwitchParameter | False | Named | False |
| ArchiverAppliance | Specifies the archiver appliance. The cmdlet will use it to transfer data from S3 compatible object storage to S3 compatible object storage with data archiving.  You can use either Windows-based or Linux-based appliance. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the folder for S3 compatible that supports data archiving.  If you do not provide this parameter and the S3 compatible object storage folder is owned by another host, you will not be able to add S3 compatible object storage to the backup infrastructure.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add S3 compatible object storage with data archiving without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRS3GlacierCompatibleRepository](vbrs3glaciercompatiblerepository.md)

Examples

Adding S3 Compatible Object Storage with Data Archiving

This example shows how to add S3 compatible object storage with data archiving to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRAmazonAccount  $connect = Connect-VBRAmazonS3CompatibleService -Account $account[0] -CustomRegionId "us-east-1" -ServicePoint "http://172.24.185.88:80" -ServiceType ArchiveTier  $folder = New-VBRAmazonS3Folder -Bucket $bucket[1] -Connection $connect -Name "TW02"  $s3Archive = Add-VBRS3GlacierCompatibleRepository -AmazonS3Folder $folder -Name "Monthly\_Reports" -Connection $connect |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Save the result to the $account variable.
2. Run the [Connect-VBRAmazonS3CompatibleService](connect-vbramazons3compatibleservice.md) cmdlet. Specify the Account, CustomRegionId, ServicePoint and the ServiceType parameter values. Save the result to the $connect variable.
3. Run the [New-VBRAmazonS3Folder](new-vbramazons3folder.md) cmdlet. Specify the Bucket, Connection and Name parameter values. Save the result to the $folder variable.
4. Run the Add-VBRS3GlacierCompatibleRepository cmdlet. Specify the following settings:

* Set the $folder variable as the AmazonS3Folder parameter value.
* Set the $connect variable as the Connection parameter value.
* Set the Name parameter value.
* Save the result to the $s3Archive variable.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3CompatibleService](connect-vbramazons3compatibleservice.md)
* [New-VBRAmazonS3Folder](new-vbramazons3folder.md)



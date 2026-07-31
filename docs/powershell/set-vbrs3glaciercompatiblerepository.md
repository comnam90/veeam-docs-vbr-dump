---
title: "Set-VBRS3GlacierCompatibleRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrs3glaciercompatiblerepository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRS3GlacierCompatibleRepository


Short Description

Modifies settings of S3 compatible object storage with data archiving.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRS3GlacierCompatibleRepository -Repository <VBRS3GlacierCompatibleRepository> [-Name <string>] [-Description <string>] [-ArchiverAppliance <CHost>] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of S3 compatible object storage with data archiving that is added to the backup infrastructure.

|  |
| --- |
| Important |
| Do NOT change the immutability settings for your S3 compatible object storage with data archiving repository, otherwise it may result in data loss in the following scenarios:   * If you provide the EnableBackupImmutability parameter to enable immutability for already configured object storage if it was not enabled beforehand. * If you provide the EnableBackupImmutability:$False parameter to disable immutability for already configured object storage if it was enabled beforehand. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Repository | Specifies an S3 compatible object storage with data archiving that you want to modify. | Accepts the [VBRS3GlacierCompatibleRepository](vbrs3glaciercompatiblerepository.md) object. To create this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of S3 compatible object storage with data archiving. The cmdlet will add S3 compatible object storage with this name. | String | False | Named | False |
| Description | Specifies a description of S3 compatible object storage with data archiving. The cmdlet will add S3 compatible object storage with this description. | String | False | Named | False |
| ArchiverAppliance | Specifies the archiver appliance. The cmdlet will use it to transfer data from S3 compatible object storage to S3 compatible object storage with data archiving. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | Defines the immutability period in days.  Default: 30 days.  Maximum: 999 days. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will add S3 compatible object storage with data archiving without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRS3GlacierCompatibleRepository](vbrs3glaciercompatiblerepository.md)

Examples

Modifying Settings for S3 Compatible Object Storage with Data Archiving

This example shows how to specify the archiver appliance for the Atlanta03 S3 compatible object storage with data archiving.

|  |
| --- |
| $appliance = Get-VBRServer -Name "WinSrv2049"  $repo = Get-VBRArchiveObjectStorageRepository -Name "Atlanta03"  $s3Glacier = Set-VBRS3GlacierCompatibleRepository -Repository $repo -ArchiverAppliance $appliance |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $appliance variable.
2. Run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repo variable.
3. Run the Set-VBRS3GlacierCompatibleRepository cmdlet. Set the $repo variable as the Repository parameter value. Set the $appliance variable as the ArchiverAppliance parameter value. Save the result to the $s3Glacier variable.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md)

Page updated 2026-05-27


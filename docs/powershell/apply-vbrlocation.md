---
title: "Apply-VBRLocation"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/apply-vbrlocation.html"
last_updated: "4/12/2024"
product_version: "13.0.1.1071"
---

# Apply-VBRLocation


Short Description

Assigns geographic locations to the backup infrastructure components.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Apply-VBRLocation -Object <Object[]> -Location <VBRLocation>  [<CommonParameters>] |

Detailed Description

This cmdlet assigns geographic locations to the backup infrastructure components.

Parameters

| Parameter | Description |  | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Object | Specifies the array of the infrastructure components. The cmdlet will assign a location to these components. | Accepts the following objects:   * CBackupRepository (backup repository). Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get this object. * [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) (scale-out backup repository). Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get this object. * [VBRTapeVault](vbrtapevault.md) (tape vault). Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet to get this object. * [VBRTapeLibrary](vbrtapelibrary.md) (tape library). Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet to get this object. * [VBRCloudProvider](vbrcloudprovider.md) (cloud provider). Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet to get this object. * [VBRProtectionGroup](vbrprotectiongroup.md) (protection group).  Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet to get this object. * [Find-VBRViEntity](find-vbrvientity.md) return types (VMware virtual objects). * [Find-VBRHvEntity](find-vbrhventity.md) return types (Hyper-V virtual objects). * [VBRAmazonS3Repository](vbramazons3repository.md) (Amazon S3 object storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. * [VBRAmazonS3CompatibleRepository](vbramazons3compatiblerepository.md) (S3 compatible object storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. * [VBRAzureBlobRepository](vbrazureblobrepository.md) (Azure Blob object storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. * [VBRAzureDataBoxRepository](vbrazuredataboxrepository.md) (Azure Data Box storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. | True | Named | True (ByProperty Name) |
| Location | Specifies the location you want to assign to the infrastructure components. | Accepts the VBRLocation object. To get this object, run the [Get-VBRLocation](get-vbrlocation.md) cmdlet. | True | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Assigning Location to Backup Repository and ESXI Host

This example shows how to assign a selected location to a backup repository and an ESXi host.

|  |
| --- |
| $rep = Get-VBRBackupRepository -Name "North Repository"  $esxi = Find-VBRViEntity -Name team.support.north  $loc = Get-VBRLocation -Name "ABC North"  Apply-VBRLocation -Objects $esxi, $rep -Location $loc |

Perform the following steps:

1. Get the infrastructure components to which you want to assign a location:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $rep variable.
2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $esxi variable.

1. Run the [Get-VBRLocation](get-vbrlocation.md) cmdlet. Specify the Name parameter value. Save the result to the $loc variable.
2. Run the Apply-VBRLocation cmdlet. Set the $esxi and the $rep variables as the Objects parameter values. Set the $loc variable as the Location parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRLocation](get-vbrlocation.md)



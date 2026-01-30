---
title: "Get-VBRLocation"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlocation.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRLocation


Short Description

Returns geographic locations created in Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get locations by name.

|  |
| --- |
| Get-VBRLocation [-Name <string[]>]  [<CommonParameters>] |

* Get locations by ID.

|  |
| --- |
| Get-VBRLocation [-Id <guid[]>]  [<CommonParameters>] |

* Get locations assigned to the backup infrastructure component.

|  |
| --- |
| Get-VBRLocation [-Object <Object>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns geographic locations created in Veeam Backup & Replication. You can get the list of all locations or search for instances directly by name, ID or associated infrastructure components.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of location names.  The cmdlet will return locations with these names. | String[] | True | Named | True (ByProperty Name) |
| Id | Specifies the array of location IDs.  The cmdlet will return locations with these IDs. | Guid[] | True | Named | True (ByProperty Name) |
| Object | Specifies the Veeam Backup & Replication infrastructure component.  The cmdlet will return a location assigned to this component. | Accepts the following objects:   * CBackupRepository (backup repository). Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get this object. * [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) (scale-out backup repository). Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get this object. * [VBRTapeVault](vbrtapevault.md) (tape vault). Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet to get this object. * [VBRTapeLibrary](vbrtapelibrary.md) (tape library). Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet to get this object. * [VBRCloudProvider](vbrcloudprovider.md) (cloud provider). Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet to get this object. * [VBRProtectionGroup](vbrprotectiongroup.md) (protection group). Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet to get this object. * Objects returned by the [Find-VBRViEntity](find-vbrvientity.md) cmdlet (VMware virtual objects). * Objects returned by the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet (Hyper-V virtual objects) * [VBRAmazonS3Repository](vbramazons3repository.md) (Amazon S3 object storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. * [VBRAmazonS3CompatibleRepository](vbramazons3compatiblerepository.md) (S3 compatible object storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. * [VBRAzureBlobRepository](vbrazureblobrepository.md) (Azure Blob object storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. * [VBRAzureDataBoxRepository](vbrazuredataboxrepository.md) (Azure Data Box storage). Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get this object. | True | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLocation object that lists geographic locations created in Veeam Backup & Replication.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Locations by Name

|  |  |
| --- | --- |
| This command returns locations by name.  |  | | --- | | Get-VBRLocation -Name "Location North", SuperLocation | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Locations by ID

|  |  |
| --- | --- |
| This command returns locations by ID.  |  | | --- | | Get-VBRLocation -Id 97e9f314-690c-410f-a1c2-acc101faa2ce, a1218a40-e863-4d38-813f-e68974c3896 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Location Assigned to ESXi Host

|  |  |
| --- | --- |
| This example shows how to get the location assigned to the ESXi host.  |  | | --- | | $esxi = Find-VBRViEntity -Name team.support.north  Get-VBRLocation -Object $esxi |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $esxi variable. 2. Run the Get-VBRLocation cmdlet. Set the $esxi variable as the Object parameter value. |

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Find-VBRHvEntity](find-vbrhventity.md)



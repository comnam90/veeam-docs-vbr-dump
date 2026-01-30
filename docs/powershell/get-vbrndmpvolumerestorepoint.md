---
title: "Get-VBRNDMPVolumeRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrndmpvolumerestorepoint.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNDMPVolumeRestorePoint


Short Description

Returns restore points of NDMP server volumes.

Applies to

Product Edition: Enterprise

Syntax

This cmdlet provides parameter sets that allow you to:

* Get restore points available for specific volumes.

|  |
| --- |
| Get-VBRNDMPVolumeRestorePoint -Volume <VBRNDMPVolume>  [<CommonParameters>] |

* Get restore points by the backup ID.

|  |
| --- |
| Get-VBRNDMPVolumeRestorePoint -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points available for NDMP server volumes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies NDMP server volumes. The cmdlet will return an array of restore points available for selected volumes. | Accepts the [VBRNDMPVolume](vbrndmpvolume.md) object. To get this object, run the [Get-VBRNDMPVolume](get-vbrndmpvolume.md) cmdlet. | True | Named | False |
| Id | Specifies an array of IDs for backups that are stored on the NDMP server. The cmdlet will return an array of selected backups. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNDMPVolumeRestorePoint](vbrndmpvolumerestorepoint.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Restore Points for NDMP Server Volume [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get the restore points available for the /svm-cifs/Exhcange\_vol volume.  |  | | --- | | $volume = Get-VBRNDMPVolume -Name "/svm-cifs/Exhcange\_vol"  Get-VBRNDMPVolumeRestorePoint -Volume $volume |  Perform the following steps:   1. Run the [Get-VBRNDMPVolume](get-vbrndmpvolume.md) cmdlet to get the volume. Specify the Name parameter value. Save the result to the $volume variable. 2. Run the Get-VBRNDMPVolumeRestorePoint cmdlet. Set the $volume variable as the Volume parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Points for NDMP Server Volume by Backup ID [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get the restore points available on the /svm-cifs/Exhcange\_vol volume by the 3efbf118-978f-4858-805d-d8560208dc6f backup ID.  |  | | --- | | $volume = Get-VBRNDMPVolume -Name "/svm-cifs/Exhcange\_vol"  Get-VBRNDMPVolumeRestorePoint -Volume $volume -ID "3efbf118-978f-4858-805d-d8560208dc6f" |  Perform the following steps:   1. Run the [Get-VBRNDMPVolume](get-vbrndmpvolume.md) cmdlet to get the volume. Specify the Name parameter value. Save the result to the $volume variable. 2. Run the Get-VBRNDMPVolumeRestorePoint cmdlet. Set the $volume variable as the Volume parameter value. Specify the ID parameter value. |

Related Commands

[Get-VBRNDMPVolume](get-vbrndmpvolume.md)



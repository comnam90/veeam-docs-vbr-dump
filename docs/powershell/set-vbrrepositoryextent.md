---
title: "Set-VBRRepositoryExtent"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrrepositoryextent.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Set-VBRRepositoryExtent

In this article

Short Description

Modifies performance extents of scale-out backup repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRRepositoryExtent -Extent <VBRRepositoryExtent[]> [-StoreFull] [-StoreIncrement] [-Data] [-Metadata]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies performance extents of a scale-out repository. You can change the backup placement mode for a selected extents to store only full backups, only incremental backups or full and incremental backups. By default, the extents are created with full and incremental backups placement mode.

|  |
| --- |
| Important |
| You cannot modify parameters of object storage performance extents using this cmdlet. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Extent | Specifies the array of extents you want to modify.  All extents must belong to the same scale-out repository. | Accepts the following object:   * GUID * String (name of the backup repository that is used as extent) * [VBRDataLocalityExtent](vbrdatalocalityextent.md) * [VBRPerformanceExtent](vbrperformanceextent.md)   To get one of these object, run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| StoreFull | For extents with Performance policy.  Defines that the extent will store only full backups.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| StoreIncrement | For extents with Performance policy.  Defines that the extent will store only incremental backups.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| Data | Defines that the extent will store only backup data.  This parameter can be used together with the Metadata parameter.  Default: False. | SwitchParameter | False | Named | True (ByValue, ByProperty Name) |
| Metadata | Defines that the extent will store only backup metadata.  Note: an extent with the metadata role can be used for storing file backups jobs metadata only.  This parameter can be used together with the Data parameter.  Default: False. | SwitchParameter | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns one of the following objects:

* [VBRDataLocalityExtent](vbrdatalocalityextent.md)
* [VBRPerformanceExtent](vbrperformanceextent.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Changing Storing Mode to Store Only Full Backups

|  |  |
| --- | --- |
| This command changes the storing mode to store only full backups for the extent named Backup Repository 1.  |  | | --- | | Set-VBRRepositoryExtent –Extent “Backup Repository 1” –StoreFull | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Storing Full and Incremental Backups

|  |  |
| --- | --- |
| This command enables storing of full and incremental backups on extents Backup Repository 1 and Backup Repository 4.  |  | | --- | | Set-VBRRepositoryExtent –Extent “Backup Repository 1”, “Backup Repository 4” –StoreFull –StoreIncrement | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Assigning Metadata and Data Roles

|  |  |
| --- | --- |
| These commands enable assigning the metadata role to extent File Backup Repository on SSD and data role to extent Backup Repository 1.  |  | | --- | | Set-VBRRepositoryExtent –Extent “File Backup Repository on SSD” -Metadata  Set-VBRRepositoryExtent –Extent “Backup Repository 1” –Data | |

Related Commands

[Get-VBRRepositoryExtent](get-vbrrepositoryextent.md)

Page updated 9/2/2025

Page content applies to build 13.0.1.1071

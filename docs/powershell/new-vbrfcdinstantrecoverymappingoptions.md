---
title: "New-VBRFCDInstantRecoveryMappingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfcdinstantrecoverymappingoptions.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# New-VBRFCDInstantRecoveryMappingOptions

In this article

Short Description

Defines mapping settings of virtual disks that you want to restore using the Instant FCD Recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define mapping settings of all backed-up virtual disks that you want to restore using the Instant FCD Recovery.

|  |
| --- |
| New-VBRFCDInstantRecoveryMappingOptions -All  [<CommonParameters>] |

* Define mapping settings of specific virtual disks that you want to restore using the Instant FCD Recovery.

|  |
| --- |
| New-VBRFCDInstantRecoveryMappingOptions -NameInBackup <string[]> -MountedDiskName <string[]> -RegisteredFCDName<string[]>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRFCDInstantRecoveryMappingOptions object. This object defines mapping settings of virtual disks that you want to restore using the Instant FCD Recovery.

Run the [Start-VBRFCDInstantRecovery](start-vbrfcdinstantrecovery.md) cmdlet to start the FCD instant recovery session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| All | Defines mapping settings for all backed-up virtual disks. | SwitchParameter | True  Note: This parameter is required only when you use the first parameter set (Define mapping settings for all disks). You do not need to specify it if you are defining settings for specific virtual disks. | Named | False |
| NameInBackup | Specifies an array of names for backed-up virtual disks. The cmdlet will define mapping settings for these disks. | String[] | True | Named | False |
| MountedDiskName | Specifies an array of names for virtual disks that that are mounted to the datastore. | String[] | True | Named | False |
| RegisteredFCDName | Specifies an array of names for FCDs that are registered on the cluster. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFCDInstantRecoveryMappingOptions object that defines mapping settings of virtual disks that you want to restore using the Instant FCD Recovery.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Mapping Settings of all Virtual Disks to Restore Using Instant FCD Recovery

|  |  |
| --- | --- |
| This command defines mapping settings of all backed-up virtual disks that you want to restore using the Instant FCD Recovery.  |  | | --- | | New-VBRFCDInstantRecoveryMappingOptions -All | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Mapping Settings of Specific Virtual Disks to Restore Using Instant FCD Recovery

|  |  |
| --- | --- |
| This command defines mapping settings of specific virtual disks that you want to restore using the Instant FCD Recovery.  |  | | --- | | New-VBRFCDInstantRecoveryMappingOptions -NameInBackup "Disk1" -MountedDiskName "RestoredDisk1" -RegisteredFCDName "FCD-Disk1" | |

Page updated 1/15/2026

Page content applies to build 13.0.1.1071

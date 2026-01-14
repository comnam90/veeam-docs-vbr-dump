---
title: "Add-VBRDiscoveredComputerRecoveryMedia"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrdiscoveredcomputerrecoverymedia.html"
last_updated: "10/9/2025"
product_version: "13.0.1.1071"
---

# Add-VBRDiscoveredComputerRecoveryMedia

In this article

Short Description

Creates Veeam Recovery Media.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRDiscoveredComputerRecoveryMedia -DiscoveredComputer <VBRDiscoveredComputer> -RecoveryMediaTarget <VBRRecoveryMediaTarget> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet creates Veeam Recovery — a recovery image of your computer. You can create Veeam Recovery Media on removable storage devices or save it locally in the ISO file format.

|  |
| --- |
| ![Add-VBRDiscoveredComputerRecoveryMedia](images/icon_note.webp) Note: |
| To create Veeam Recovery Media for a protected computer, you must have a full backup of this computer. This backup must contain an OS of this computer. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies the discovered computer for which you want to create Veeam Recovery Media.  Note: You can create Veeam Recovery Media only for discovered computers. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue ByProperty Name) |
| RecoveryMediaTarget | Specifies a storage device or the ISO file path for creating Veeam Recovery Media. | Accepts the VBRRecoveryMediaTarget object. To get this object, run the [Get-VBRRecoveryMediaTarget](get-vbrrecoverymediatarget.md) cmdlet. | True | Named | True (ByProperty Name) |
| Force | Defines that the cmdlet will create Veeam Recovery Media even if any of the following occurs:   * The target removable device needs to be formatted. * The ISO file under the specified path already exists. * There is not enough space on the target removable device. | SwitchParameter | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRProtectionGroup](vbrprotectiongroup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Saving Veeam Recovery Media in ISO File Format

|  |  |
| --- | --- |
| This example shows how to save Veeam Recovery Media in the ISO file format.  |  | | --- | | $isopath = New-VBRRecoveryMediaISOTarget -Path "c:\image.iso"  $computer = Get-VBRDiscoveredComputer | Where {$\_.name -eq "support.east.local"}  Add-VBRDiscoveredComputerRecoveryMedia -DiscoveredComputer $computer -RecoveryMediaTarget $isopath |  Perform the following steps:   1. Run the [New-VBRRecoveryMediaISOTarget](new-vbrrecoverymediaisotarget.md) cmdlet. Specify the Path parameter value. Save the result to the $isopath variable. 2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Use the Where-Object method to get the computer for which you want to create Veeam Recovery Media. Save the result to the $computer variable. 3. Run the Add-VBRDiscoveredComputerRecoveryMedia cmdlet. Set the $computer variable as the DiscoveredComputer parameter value. Set the $isopath variable as the RecoveryMediaTarget parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Veeam Recovery Media on Removable Storage Device

|  |  |
| --- | --- |
| This example shows how to create Veeam Recovery Media on a removable storage device.  |  | | --- | | $computer = Get-VBRDiscoveredComputer | Where {$\_.name -eq "support.east.local"}  $removable = Get-VBRRecoveryMediaTarget -Type RemovableDevice | Where {$\_.Description -eq "RECOVERY (F:)"}  Add-VBRDiscoveredComputerRecoveryMedia -DiscoveredComputer $computer -RecoveryMediaTarget $removable |  Perform the following steps:   1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Use the Where-Object method to get the computer for which you want to create Veeam Recovery Media. Save the result to the $computer variable. 2. Run the [Get-VBRRecoveryMediaTarget](get-vbrrecoverymediatarget.md) cmdlet. Set the RemovableDevice value as the Type parameter value. Use the Where-Object method to get the removable storage device where you want to create Veeam Recovery Media. Save the result to the $removable variable. 3. Run the Add-VBRDiscoveredComputerRecoveryMedia cmdlet. Set the $computer variable as the DiscoveredComputer parameter value. Set the $removable variable as the RecoveryMediaTarget parameter value. |

Related Commands

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRRecoveryMediaTarget](get-vbrrecoverymediatarget.md)
* [New-VBRRecoveryMediaISOTarget](new-vbrrecoverymediaisotarget.md)

Page updated 10/9/2025

Page content applies to build 13.0.1.1071

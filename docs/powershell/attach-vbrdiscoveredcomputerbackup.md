---
title: "Attach-VBRDiscoveredComputerBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/attach-vbrdiscoveredcomputerbackup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Attach-VBRDiscoveredComputerBackup


Short Description

Allows a discovered computer to access a backup.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Attach-VBRDiscoveredComputerBackup -Computer <VBRDiscoveredComputer> -Backup <VBRDiscoveredComputerBackup>  [<CommonParameters>] |

Detailed Description

This cmdlet allows a discovered computer to access a backup. The cmdlet grants the specified discovered computer access to the specified backup.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Computer | Specifies the discovered computer that you want to allow to access the backup. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Backup | Specifies the backup that you want to allow the discovered computer to access. | Accepts the [VBRDiscoveredComputerBackup](vbrdiscoveredcomputerbackup.md) object. To get this object, run the [Get-VBRDiscoveredComputerBackup](get-vbrdiscoveredcomputerbackup.md) cmdlet. | True | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Allowing Discovered Computer to Access Backup

This example shows how to allow a discovered computer to access a backup.

|  |
| --- |
| $computer = Get-VBRDiscoveredComputer | Where {$\_.Name -eq "support.east.local"}  $backup = Get-VBRDiscoveredComputerBackup -Computer $computer  Attach-VBRDiscoveredComputerBackup -Computer $computer -Backup $backup |

Perform the following steps:

1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Use the Where-Object method to get the necessary discovered computer. Save the result to the $computer variable.
2. Run the [Get-VBRDiscoveredComputerBackup](get-vbrdiscoveredcomputerbackup.md) cmdlet. Set the $computer variable as the Computer parameter value. Save the result to the $backup variable.
3. Run the Attach-VBRDiscoveredComputerBackup cmdlet. Set the $computer variable as the Computer parameter value. Set the $backup variable as the Backup parameter value.

Related Commands

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRDiscoveredComputerBackup](get-vbrdiscoveredcomputerbackup.md)

Page updated 2026-06-04


---
title: "Detach-VBRDiscoveredComputerBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/detach-vbrdiscoveredcomputerbackup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Detach-VBRDiscoveredComputerBackup


Short Description

Revokes a discovered computer's access to a backup.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Detach-VBRDiscoveredComputerBackup -Computer <VBRDiscoveredComputer> -Backup <VBRDiscoveredComputerBackup>  [<CommonParameters>] |

Detailed Description

This cmdlet revokes a discovered computer's access to a backup. The cmdlet removes the specified discovered computer's access to the specified backup.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Computer | Specifies the discovered computer whose access to the backup you want to revoke. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Backup | Specifies the backup that you want to revoke the discovered computer's access to. | Accepts the [VBRDiscoveredComputerBackup](vbrdiscoveredcomputerbackup.md) object. To get this object, run the [Get-VBRDiscoveredComputerBackup](get-vbrdiscoveredcomputerbackup.md) cmdlet. | True | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Revoking Discovered Computer Access to Backup

This example shows how to revoke a discovered computer's access to a backup.

|  |
| --- |
| $computer = Get-VBRDiscoveredComputer | Where {$\_.Name -eq "support.east.local"}  $backup = Get-VBRDiscoveredComputerBackup -Computer $computer  Detach-VBRDiscoveredComputerBackup -Computer $computer -Backup $backup |

Perform the following steps:

1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Use the Where-Object method to get the necessary discovered computer. Save the result to the $computer variable.
2. Run the [Get-VBRDiscoveredComputerBackup](get-vbrdiscoveredcomputerbackup.md) cmdlet. Set the $computer variable as the Computer parameter value. Save the result to the $backup variable.
3. Run the Detach-VBRDiscoveredComputerBackup cmdlet. Set the $computer variable as the Computer parameter value. Set the $backup variable as the Backup parameter value.

Related Commands

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRDiscoveredComputerBackup](get-vbrdiscoveredcomputerbackup.md)

Page updated 2026-06-04


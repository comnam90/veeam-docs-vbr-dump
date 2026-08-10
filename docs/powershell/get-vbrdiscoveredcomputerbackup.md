---
title: "Get-VBRDiscoveredComputerBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdiscoveredcomputerbackup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRDiscoveredComputerBackup


Short Description

Returns backups of discovered computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all backups that a discovered computer can access.

|  |
| --- |
| Get-VBRDiscoveredComputerBackup -Computer <VBRDiscoveredComputer> [<CommonParameters>] |

* Get the discovered computers that have permission to access a specific backup.

|  |
| --- |
| Get-VBRDiscoveredComputerBackup -Backup <VBRBackup> [<CommonParameters>] |

Detailed Description

This cmdlet returns backups of discovered computers created with Veeam Agent backup policies. You can get all backups that a specific discovered computer can access, or get the discovered computers that have permission to access a specific backup.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Computer | Specifies the discovered computer whose backups you want to get. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Backup | Specifies the backup. The cmdlet returns the discovered computers that have permission to access this backup. | Accepts the VBRBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns an array of [VBRDiscoveredComputerBackup](vbrdiscoveredcomputerbackup.md) objects that represent backups of discovered computers.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Backups of Discovered Computer

|  |  |
| --- | --- |
| This example shows how to get all the backups that a discovered computer can access.  |  | | --- | | $computer = Get-VBRDiscoveredComputer | Where {$\_.Name -eq "support.east.local"}  Get-VBRDiscoveredComputerBackup -Computer $computer |  Perform the following steps:   1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Use the Where-Object method to get the necessary discovered computer. Save the result to the $computer variable. 2. Run the Get-VBRDiscoveredComputerBackup cmdlet. Set the $computer variable as the Computer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Discovered Computers with Access to Backup

|  |  |
| --- | --- |
| This example shows how to get a backup and return which discovered computers have permission to access this backup.  |  | | --- | | $parent = Get-VBRBackup | Where-Object Name -eq "Mac1 DBOS"  Get-VBRDiscoveredComputerBackup -Backup $parent |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Use the Where-Object method to get the necessary backup. Save the result to the $parent variable. 2. Run the Get-VBRDiscoveredComputerBackup cmdlet. Set the $parent variable as the Backup parameter value. |

Related Commands

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRBackup](get-vbrbackup.md)

Page updated 2026-06-23


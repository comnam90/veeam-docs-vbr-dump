---
title: "New-VBRComputerIndexingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcomputerindexingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRComputerIndexingOptions

In this article

Short Description

Creates indexing settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRComputerIndexingOptions -BackupObject <Object> -OSPlatform <VBRAgentType> {Windows | Linux | Mac} -IndexingMode <VBRIndexingMode> {Disable | IndexEverything | IndexIncludedOnly | IndexEverythingExceptExcluded} [-IndexingInclusion <string[]>] [-IndexingExclusion <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRComputerIndexingOptions object. This object contains file indexing settings for Veeam Agent backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies the protection group, for which you want to add indexing settings. | Accepts the Object object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue) |
| OSPlatform | Specifies the OS of the protected computers:   * Windows: for Windows computers. * Linux: for Linux computers. * Mac: for macOS computers. | VBRAgentType | True | Named | False |
| IndexingMode | Specifies indexing scope settings:   * Disable: select this option to disable indexing mode. * IndexEverything: select this option to index all files within the backup scope. * IndexIncludedOnly: select this option to specify folders that you want to index. * IndexEverythingExceptExcluded: select this option to index all directories on the protected computer except for those you want to exclude from indexing.  Note: Not available for the backup policy that Veeam Agent job applies to Linux machines with file-level backup scope.   Note: Veeam Backup & Replication will exclude the system directories from indexing. | VBRIndexingMode | True | Named | False |
| IndexingInclusion | For the IndexIncludedOnly mode.  Specifies the list of the folders that you want to index. | String[] | False | Named | False |
| IndexingExclusion | For the IndexEverythingExceptExcluded mode.  Specifies the list of the folders that you want to exclude from indexing. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerIndexingOptions object that contains file indexing settings for Veeam Agent backup jobs.

Examples

Creating Indexing Settings for Veeam Agent Backup Job (Linux)

This example shows how to create indexing settings for a Veeam Agent job that backs up Linux computers. Veeam Backup & Replication will index everything except for:

* System directories.
* The /home/administrator/videos/ directory.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Linux Group"  New-VBRComputerIndexingOptions -BackupObject $group -OSPlatform Linux -IndexingMode IndexEverythingExceptExcluded -IndexingExclusion "/home/administrator/videos/" |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the New-VBRComputerIndexingOptions cmdlet. Specify the following settings:

* Set the $group variable as the BackupObject parameter value.
* Set the Linux option for the OSPlatform parameter.
* Set the IndexEverythingExceptExcluded option for the IndexingMode parameter.
* Specify the IndexingExclusion parameter value.

Related Commands

[Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071

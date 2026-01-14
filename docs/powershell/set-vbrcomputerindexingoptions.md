---
title: "Set-VBRComputerIndexingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputerindexingoptions.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerIndexingOptions

In this article

Short Description

Modifies indexing settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerIndexingOptions -Options <VBRComputerIndexingOptions> [-IndexingMode <VBRIndexingMode> {Disable | IndexEverything | IndexIncludedOnly | IndexEverythingExceptExcluded}] [-IndexingInclusion <string[]>] [-IndexingExclusion <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies indexing settings for Veeam Agent backup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the protection group indexing options that you want to modify. | Accepts the VBRComputerIndexingOptions object. To get this object, run the [New-VBRComputerIndexingOptions](new-vbrcomputerindexingoptions.md) cmdlet. | True | Named | True (ByValue) |
| IndexingMode | Specifies indexing scope settings:   * Disable: select this option to disable indexing mode. * IndexEverything: select this option to index all files within the backup scope. * IndexIncludedOnly: select this option to specify folders that you want to index. * IndexEverythingExceptExcluded: select this option to index all directories on the protected computer except for those you want to exclude from indexing.   Note: Veeam Backup & Replication will exclude the system directories from indexing. | VBRIndexingMode | False | Named | False |
| IndexingInclusion | For the IndexIncludedOnly mode.  Specifies the list of the folders that you want to index. | String[] | False | Named | False |
| IndexingExclusion | For the IndexEverythingExceptExcluded mode.  Specifies the list of the folders that you want to exclude from indexing. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerIndexingOptions object that contains file indexing settings for Veeam Agent backup jobs.

Examples

Modifying Indexing Settings for Veeam Agent Backup Job (Windows)

This example shows how to modify indexing settings for a Veeam Agent job that backs up Windows computers. Veeam Backup & Replication will change the indexing scope and will index everything except for system folders.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Windows Group"  $index = New-VBRComputerIndexingOptions -BackupObject $group -OSPlatform Windows -IndexingMode IndexIncludedOnly -IndexingInclusion "C:/Desktop/MyFolder"  Set-VBRComputerIndexingOptions -Options $index -IndexingMode IndexEverything |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value Save the result to the $group variable.
2. Run the [New-VBRComputerIndexingOptions](new-vbrcomputerindexingoptions.md) cmdlet. Set the $group variable as the BackupObject parameter value. Specify the OSPlatform, IndexingMode and IndexingInclusion parameter values. Save the result to the $index variable.
3. Run the Set-VBRComputerIndexingOptions cmdlet. Set the $index variable as the Options parameter value. Set the IndexEverything option for the IndexingMode parameter.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [New-VBRComputerIndexingOptions](new-vbrcomputerindexingoptions.md)

Page updated 3/8/2024

Page content applies to build 13.0.1.1071

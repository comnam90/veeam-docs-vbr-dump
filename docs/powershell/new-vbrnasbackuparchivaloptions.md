---
title: "New-VBRNASBackupArchivalOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnasbackuparchivaloptions.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# New-VBRNASBackupArchivalOptions (obsolete)

In this article

Short Description

Defines long-term retention policy for file versions of backed up files from file shares.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRNASBackupArchivalOptions [-ArchivalType <VBRNASBackupArchivalType> {All | InclusionMask | ExclusionMask}] [-InclusionMask <string[]>] [-ExclusionMask <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines long-term retention policy for file versions of backed up files from file shares.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ArchivalType | Specifies the filter settings for file versions that must be kept on the long-term repository. You can specify either of the following filter settings:   * All: use this option if you want to keep all types of file versions on the long-term repository. * InclusionMask: use this option if you want to keep only file versions with specific extensions on the long-term repository. * ExclusionMask: use this option if you do not want to keep file versions with specific extensions on the long-term repository. | VBRNASBackupArchivalType | False | Named | False |
| InclusionMask | For the ArchivalType parameter with the InclusionMask value.  Specifies a file mask for files and folders that you want to add to the file backup job. The cmdlet will back up only these files and folders. | String[] | False | Named | False |
| ExclusionMask | For the ArchivalType parameter with the ExclusionMask value.  Specifies a file mask for files and folders that you do not want to add to the file backup job. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASBackupArchivalOptions](vbrnasbackuparchivaloptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Retention Policy for Active File Versions of File Share Backed Up Files by Using Filter Settings

|  |  |
| --- | --- |
| This command shows how to define retention policy for active file versions of backed up files from file shares. The long-term repository will keep only .PDF and .DOCX file extensions.    |  | | --- | | New-VBRNASBackupArchivalOptions -ArchivalType InclusionMask -InclusionMask ('\*.pdf', '\*.docx') | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Retention Policy for Deleted File Versions of File Share Backed Up Files by Using Filter Settings

|  |  |
| --- | --- |
| This command shows how to define retention policy for deleted file versions of backed up files from file shares. The long-term repository will not keep .EXE file extensions.      |  | | --- | | New-VBRNASBackupArchivalOptions -ArchivalType ExclusionMask -ExclusionMask '\*.exe' | |

Page updated 1/6/2025

Page content applies to build 13.0.1.1071

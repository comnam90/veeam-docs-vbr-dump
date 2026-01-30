---
title: "New-VBRUnstructuredBackupArchivalOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrunstructuredbackuparchivaloptions.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRUnstructuredBackupArchivalOptions


Short Description

Defines a scope of file versions to keep on an archive repository for file backup job or object storage backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRUnstructuredBackupArchivalOptions [-ArchivalType <VBRUnstructuredBackupArchivalType> {All | InclusionMask | ExclusionMask}] [-InclusionMask <string[]>] [-ExclusionMask <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines a scope of file versions backed-up by file backup job or object storage backup job to keep on an archive repository. You can include all files, define certain files to keep on archive repository or exclude certain files from the repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ArchivalType | Specifies the filter settings for file versions that you want to keep on the archive repository. You can specify one of the following filter settings:   * All: use this option if you want to keep all types of file versions on the archive repository. * InclusionMask: use this option if you want to keep only file versions with specific extensions on the archive repository. * ExclusionMask: use this option if you do not want to keep file versions with specific extensions on the archive repository. | VBRUnstructuredBackupArchivalType | False | Named | False |
| InclusionMask | For the ArchivalType parameter with the InclusionMask value.  Specifies a file mask for files and folders that you want to add to the file backup job or object storage backup job. The cmdlet will back up only these files and folders. | String[] | False | Named | False |
| ExclusionMask | For the ArchivalType parameter with the ExclusionMask value.  Specifies a file mask for files and folders that you do not want to add to the file backup job or object storage backup job. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupArchivalOptions object that contains scope settings of files to keep on an archive repository for file backup job or object storage backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Scope of Files to Keep on Archive Repository

|  |  |
| --- | --- |
| This command defines a scope of file versions to keep on archive repositories. The archive repository will keep only file versions with PDF and DOCX extensions.  |  | | --- | | New-VBRUnstructuredBackupArchivalOptions -ArchivalType InclusionMask -InclusionMask ('\*.pdf', '\*.docx') | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Excluding Files from Backup Scope

|  |  |
| --- | --- |
| This command excludes a scope of file versions. The archive repository will not keep .EXE file extensions.      |  | | --- | | New-VBRUnstructuredBackupArchivalOptions -ArchivalType ExclusionMask -ExclusionMask '\*.exe' | |



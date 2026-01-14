---
title: "Set-VBRNASBackupArchivalOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasbackuparchivaloptions.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Set-VBRNASBackupArchivalOptions (obsolete)

In this article

Short Description

Modifies retention policy for file versions.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Set-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASBackupArchivalOptions -Options <VBRNASBackupArchivalOptions> [-ArchivalType <VBRNASBackupArchivalType> {All | InclusionMask | ExclusionMask}] [-InclusionMask <string[]>] [-ExclusionMask <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of retention policy for file versions that are kept on the long-term repository.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the retention policy for file versions. The cmdlet will modify the settings of this policy. | Accepts the VBRNASBackupArchivalOptions object. To create this object, run the [New-VBRNASBackupArchivalOptions](new-vbrnasbackuparchivaloptions.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ArchivalType | Specifies the filter settings for file versions that must be kept on the long-term repository. You can specify either of the following filter settings:   * All: use this option if you want to keep all types of file versions on the long-term repository. * InclusionMask: use this option if you want to keep only file versions with specific extensions on the long-term repository. * ExclusionMask: use this option if you do not want to keep file versions with specific extensions on the long-term repository. | VBRNASBackupArchivalType | False | Named | False |
| InclusionMask | For the ArchivalType parameter with the InclusionMask value.  Specifies a file mask for files and folders that you want to add to the file backup job. The cmdlet will back up only these files and folders. | String[] | False | Named | False |
| ExclusionMask | For the ArchivalType parameter with the ExclusionMask value.  Specifies a file mask for files and folders that you do not want to add to the file backup job. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASBackupArchivalOptions](vbrnasbackuparchivaloptions.md)

Examples

Modifying Filter Settings of Retention Policy for Deleted File Versions

This example shows how to modify filter settings of the retention policy for deleted file versions. The retention policy will have the following settings:

* The long-term repository will keep .DOCX and .PDF file extensions.
* The long-term repository will not keep .EXE and .JPEG  file extensions.

|  |
| --- |
| $archiveOptions = New-VBRNASBackupArchivalOptions -ArchivalType ExclusionMask -ExclusionMask ('\*.jpeg', '\*.exe')  $newArchiveOptions = Set-VBRNASBackupArchivalOptions -Options $archiveOptions -ArchivalType InclusionMask -InclusionMask ('\*.docx', '\*.pdf') |

Perform the following steps:

1. Run the [New-VBRNASBackupArchivalOptions](new-vbrnasbackuparchivaloptions.md) cmdlet. Specify the ExclusionMask parameter value. Save the result to the $archiveOptions variable.
2. Run the Set-VBRNASBackupArchivalOptions cmdlet. Specify the following settings:

* Set the $archiveoptions variable as the Options parameter value.
* Set the InclusionMask as the ArchivalType parameter value.
* Specify the InclusionMask parameter value.
* Save the result to the $newArchiveOptions variable to be used with other cmdlets.

Related Commands

[New-VBRNASBackupArchivalOptions](new-vbrnasbackuparchivaloptions.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071

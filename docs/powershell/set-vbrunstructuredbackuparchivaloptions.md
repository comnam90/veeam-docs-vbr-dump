---
title: "Set-VBRUnstructuredBackupArchivalOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrunstructuredbackuparchivaloptions.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRUnstructuredBackupArchivalOptions


Short Description

Modifies a scope of file versions to keep on an archive repository for file backup job or object storage backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRUnstructuredBackupArchivalOptions -Options <VBRUnstructuredBackupArchivalOptions> [-ArchivalType <VBRUnstructuredBackupArchivalType> {All | InclusionMask | ExclusionMask}] [-InclusionMask <string[]>] [-ExclusionMask <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a scope of file versions to keep on an archive repository for file backup job or object storage backup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the scope of file versions. The cmdlet will modify this scope. | Accepts the VBRUnstructuredBackupArchivalOptions object. To create this object, run the [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ArchivalType | Specifies the filter settings for file versions that you want to keep on the archive repository. You can specify one of the following filter settings:   * All: use this option if you want to keep all types of file versions on the archive repository. * InclusionMask: use this option if you want to keep only file versions with specific extensions on the archive repository. * ExclusionMask: use this option if you do not want to keep file versions with specific extensions on the archive repository. | VBRUnstructuredBackupArchivalType | False | Named | False |
| InclusionMask | For the ArchivalType parameter with the InclusionMask value.  Specifies a file mask for files and folders that you want to add to the file backup job or object storage backup job. The cmdlet will back up only these files and folders. | String[] | False | Named | False |
| ExclusionMask | For the ArchivalType parameter with the ExclusionMask value.  Specifies a file mask for files and folders that you do not want to add to the file backup job or object storage backup job. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupArchivalOptions object that contains scope settings of files to keep on an archive repository for file backup job or object storage backup job.

Example

Modifying Scope of File Versions

This example shows how to modify a scope of file versions that are located on an archive repository. The archive repository will have the following file version settings:

* The long-term repository will keep .DOCX and .PDF file extensions.
* The long-term repository will not keep .EXE and .JPEG  file extensions.

|  |
| --- |
| $archiveoptions = New-VBRUnstructuredBackupArchivalOptions -ArchivalType ExclusionMask -ExclusionMask ('\*.jpeg', '\*.exe')  Set-VBRUnstructuredBackupArchivalOptions -Options $archiveoptions -ArchivalType InclusionMask -InclusionMask ('\*.docx', '\*.pdf') |

Perform the following steps:

1. Run the [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet. Specify the ArchivalType and ExclusionMask parameters values. Save the result to the $archiveoptions variable.
2. Run the Set-VBRUnstructuredBackupArchivalOptions cmdlet. Specify the following settings:

* Set the $archiveoptions variable as the Options parameter value.
* Set the InclusionMask as the ArchivalType parameter value.
* Specify the InclusionMask parameter value.

Related Commands

[New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md)



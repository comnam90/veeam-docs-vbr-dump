---
title: "Set-VBRNASBackupJobObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasbackupjobobject.html"
last_updated: "4/29/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNASBackupJobObject


Short Description

Modifies settings of files and folders that will be added to the file backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASBackupJobObject -JobObject <VBRNASBackupJobObject> [-InclusionMask <String[]>] [-ExclusionMask <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of files and folders that will be added to the file backup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| JobObject | Specifies the settings of files and folders that will be added to the file backup job. The cmdlet will modify these settings. | Accepts the VBRNASBackupJobObject object. To create this object, run the [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| InclusionMask | Specifies a file mask for folders and files that you want to add to the file backup job. The cmdlet will back up only folders and files specified in this file mask. | String[] | False | Named | False |
| ExclusionMask | Specifies a file mask for folders and files that you do not want to add to the file backup job. The cmdlet will not back up these folders and files. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupJobObject object that contains settings of files and folders that will be added to the file backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Included Files

|  |  |
| --- | --- |
| This example shows how to modify settings of a file mask for files that you want to add to the file backup job. The job will back up only .DOCX and .PDF files that are located in the \\WinSRV2049\Documents\January folder.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  $files = New-VBRNASBackupJobObject -Server $server -Path "\\WinSRV2049\Documents\January" -InclusionMask "\*.docx"  $modifiedFiles = Set-VBRNASBackupJobObject -JobObject $files -InclusionMask ("\*.docx", "\*.pdf") |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md) cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the InclusionMask parameter value. * Save the result to the $files variable.  1. Run the Set-VBRNASBackupJobObject cmdlet. Set the $files as the JobObject parameter. Specify the InclusionMask parameter value. Save the result to the $modifiedFiles variable to be used with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Excluded Files

|  |  |
| --- | --- |
| This example shows how to modify settings of file mask for files that you want to exclude from the file backup job. The job will not back up .EXE files that are located in the \\WinSRV2049\Documents\January folder.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  $files = New-VBRNASBackupJobObject -Server $server -Path "\\WinSRV2049\Documents\January" -ExclusionMask "\*.exe"  $modifiedFiles = Set-VBRNASBackupJobObject -JobObject $files -ExclusionMask "\*.exe" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md) cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the ExclusionMask parameter value.  * Save the result to the $files variable.  1. Run the Set-VBRNASBackupJobObject cmdlet. Set the $files as the JobObject parameter. Specify the ExclusionMask parameter value. Save the result to the $modifiedFiles variable to be used with other cmdlets. |

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md)



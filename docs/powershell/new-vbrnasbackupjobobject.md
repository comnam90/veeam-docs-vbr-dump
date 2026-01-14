---
title: "New-VBRNASBackupJobObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnasbackupjobobject.html"
last_updated: "4/29/2024"
product_version: "13.0.1.1071"
---

# New-VBRNASBackupJobObject

In this article

Short Description

Defines settings of files and folders and enterprise NAS system that will be added to the file backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define settings of files and folders that will be added to the file backup job.

|  |
| --- |
| New-VBRNASBackupJobObject -Server <VBRNASServer> [-Path <String>] [-InclusionMask <String[]>] [-ExclusionMask <String[]>]  [<CommonParameters>] |

* Define settings of enterprise NAS system that will be added to the file backup job.

|  |
| --- |
| New-VBRNASBackupJobObject -SANEntity <VBRSANEntity> [-InclusionMask <String[]>] [-ExclusionMask <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRNASBackupJobObject object. This object contains settings of files and folders and enterprise NAS system that will be added to the file backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the server with the file share. | Accepts the VBRNASServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| SANEntity | Specifies a name of an enterprise NAS system. The cmdlet will return an array of file shares residing on this NAS system. | Accepts the VBRSANEntity object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| Path | Specifies a path to folders and files. | String | True | Named | False |
| InclusionMask | Specifies a file mask for folders and files that you want to add to the file backup job. The cmdlet will back up only folders and files specified in this file mask. | String[] | False | Named | False |
| ExclusionMask | Specifies a file mask for folders and files that you do not want to add to the file backup job. The cmdlet will not back up these folders and files. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupJobObject object that contains settings of files and folders that will be added to the file backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Folders to Add to File Backup Job

|  |  |
| --- | --- |
| This example shows how to define folders that you want to add to the file backup job. The job will back up all files that are located in the \\WinSRV2049\Documents\January folder.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  New-VBRNASBackupJobObject -Server $server -Path "//WinSRV2049/Documents/January" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the New-VBRNASBackupJobObject cmdlet. Set the $server variable as the Server parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Included Files to Add to File Backup Job

|  |  |
| --- | --- |
| This example shows how to define a mask for files that you want to add to the file backup job. The job will back up only .DOCX files that are located in the \\WinSRV2049\Documents\January folder.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  New-VBRNASBackupJobObject -Server $server -Path "//WinSRV2049/Documents/January" -InclusionMask "\*.docx" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the New-VBRNASBackupJobObject cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the InclusionMask parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Excluded Files to Add to File Backup Job

|  |  |
| --- | --- |
| This example shows how to define a mask for files that you want to exclude from the file backup job. The job will not back up .EXE files that are located in the \\WinSRV2049\Documents\January folder.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  New-VBRNASBackupJobObject -Server $server -Path "//WinSRV2049/Documents/January" -ExclusionMask "\*.exe" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the New-VBRNASBackupJobObject cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the ExclusionMask parameter value. |

Related Commands

[Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)

Page updated 4/29/2024

Page content applies to build 13.0.1.1071

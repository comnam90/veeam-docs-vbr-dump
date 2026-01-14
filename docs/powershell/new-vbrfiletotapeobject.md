---
title: "New-VBRFileToTapeObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfiletotapeobject.html"
last_updated: "12/29/2025"
product_version: "13.0.1.1071"
---

# New-VBRFileToTapeObject

In this article

Short Description

Defines settings of the source for the files to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRFileToTapeObject -NASServer <VBRUnstructuredServer> [-Path <String>] [-IncludeMask <string>] [-ExcludeMask <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRFileToTapeObject](vbrfiletotapeobject.md) object. This object contains settings of files or directories that you want to add to a file to tape job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| NASServer | Specifies network shared folders and file servers. Veeam Backup & Replication will back up these shared folders and file servers with the file to tape job. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| Path | Specifies the target file path. | String | False | Named | False |
| IncludeMask | Specifies files that you want to back up with the file to tape job. | String | False | Named | False |
| ExcludeMask | Specifies files that you want to exclude from the file to tape job. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFileToTapeObject](vbrfiletotapeobject.md)

Examples

Creating Object for File to Tape Job

This example shows how to create an object for a file to tape job. The object contains a folder on the fileserver08 server.

|  |
| --- |
| $server = Get-VBRUnstructuredServer -Name "fileserver08.tech.local"  $folder = New-VBRFileToTapeObject -NASServer $server -Path "D:\Summary Reports\Payroll Reports" |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the New-VBRFileToTapeObject cmdlet. Set the $server variable as the NASServer parameter value. Specify the Path parameter value. Save the result to the $folder variable to be used with other cmdlets.

Related Commands

[Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)

Page updated 12/29/2025

Page content applies to build 13.0.1.1071

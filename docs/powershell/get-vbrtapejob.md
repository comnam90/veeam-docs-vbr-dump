---
title: "Get-VBRTapeJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapejob.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeJob

In this article

Short Description

Returns tape jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRTapeJob [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns tape jobs created on this Veeam backup server.

You can get backup to tape jobs, file to tape and object to tape jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of tape job names. The cmdlet will return tape jobs with these names. | String | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRBackupToTapeJob](vbrbackuptotapejob.md)
* [VBRFileToTapeJob](vbrfiletotapejob.md)
* [VBRObjectToTapeJob](vbrobjecttotapejob.md)

Examples

Getting Tape Job by Name

This command returns the tape job named Daily WebApp Backup.

|  |
| --- |
| Get-VBRTapeJob -Name "Daily WebApp Backup" |

Page updated 5/12/2025

Page content applies to build 13.0.1.1071

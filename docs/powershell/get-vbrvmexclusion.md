---
title: "Get-VBRVMExclusion"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvmexclusion.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRVMExclusion

In this article

Short Description

Returns a list of global VM exclusions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an exclusion by ID.

|  |
| --- |
| Get-VBRVMExclusion [-Id <Guid[]>]  [<CommonParameters>] |

* Get a list of exclusions by VM name or note added to the exclusion.

|  |
| --- |
| Get-VBRVMExclusion [-Name <String[]>] [-Note <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of global exclusions created for VMs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the ID of an exclusion. | Guid[] | False | 0 | True (ByPropertyName, ByValue) |
| Name | Specifies an array of excluded VM names. | String[] | False | 0 | True (ByPropertyName, ByValue) |
| Note | Specifies the note added for an exclusion. | String | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVMExclusion[] object that defines the exclusions.

Examples

Getting Exclusion by VM Name

This command returns an exclusion created for the ubuntusrv20 VM.

|  |
| --- |
| Get-VBRVMExclusion -Name "ubuntusrv20" |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071

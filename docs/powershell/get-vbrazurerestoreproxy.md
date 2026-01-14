---
title: "Get-VBRAzureRestoreProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurerestoreproxy.html"
last_updated: "5/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAzureRestoreProxy

In this article

Short Description

Returns a restore proxy appliance for restoring backups to Microsoft Azure VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureRestoreProxy [-Name <string>] [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a restore proxy appliance for restoring backups to Microsoft Azure VMs.

|  |
| --- |
| Note |
| Consider the following:   * If you specify the Id parameter, the cmdlet looks for an exact match and returns a single object. * If you specify the Name parameter, the cmdlet searches for the first proxy that matches the specified name. Note that the name is case-insensitive. * If you do not specify parameters, the cmdlet returns all Azure restore proxies added to the backup infrastructure. * If you provide both parameters, the ID parameter takes precedence. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of the restore proxy appliance that you want to get. | String | False | Named | True |
| Id | Specifies an ID of the restore proxy appliance that you want to get. | String | False | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureRestoreProxy](vbrazurerestoreproxy.md)

Examples

Getting Microsoft Azure Restore Proxy Appliance

This command shows how to get the restore proxy appliance by its name.

|  |
| --- |
| Get-VBRAzureRestoreProxy -Name "AzureProxy-01" |

Page updated 5/30/2025

Page content applies to build 13.0.1.1071

---
title: "Get-VBRApplicationGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationgroup.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# Get-VBRApplicationGroup

In this article

Short Description

Returns VMware and Hyper-V application groups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRApplicationGroup [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns VMware and Hyper-V application groups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of an application group. The cmdlet will return the application group with the specified name. | String[] | False | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRApplicationGroup object that contains settings of application groups for SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Application Groups

|  |  |
| --- | --- |
| This command returns application groups that are added to the Veeam Backup & Replication infrastructure. The cmdlet output will contain the details about the Name and the Description of application groups.  |  | | --- | | Get-VBRApplicationGroup  Name                 Description  ----                 -----------  Exchange Group       AppGroup for Exchange verification  SQL Group            AppGroup for SQL verification  File Server Group    AppGroup for File Server verification | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Application Group by Name

|  |  |
| --- | --- |
| This command returns the AppGroup for SQL verification application group. The cmdlet output will contain the details about the Name and the Description of an application group.  |  | | --- | | Get-VBRApplicationGroup -Name "Exchange Application Group"  Name                 Description  ----                 -----------  Exchange Group       AppGroup for Exchange verification | |

Page updated 4/30/2024

Page content applies to build 13.0.1.1071

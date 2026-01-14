---
title: "Get-VSBApplicationGroup (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vsbapplicationgroup.html"
last_updated: "2/26/2024"
product_version: "13.0.1.1071"
---

# Get-VSBApplicationGroup (obsolete)

In this article

Short Description

Returns application groups.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VSBApplicationGroup [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing application groups.

You can get the list of all application groups, or search for instances directly by name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of application group names. The cmdlet will return application groups with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Application Groups

|  |  |
| --- | --- |
| This command looks for the list of all application groups.  |  | | --- | | Get-VSBApplicationGroup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Application Group

|  |  |
| --- | --- |
| This command looks for the MailServer Appgroup application group.  |  | | --- | | Get-VSBApplicationGroup -Name "MailServer Appgroup" | |

Page updated 2/26/2024

Page content applies to build 13.0.1.1071

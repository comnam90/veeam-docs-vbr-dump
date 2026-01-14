---
title: "Get-VBREPSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrepsession.html"
last_updated: "1/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBREPSession

In this article

Short Description

Returns sessions of backup jobs run by Veeam Agent operating in a standalone mode.

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all sessions of backup jobs run by Veeam Agent operating in a standalone mode.

|  |
| --- |
| Get-VBREPSession  [<CommonParameters>] |

* Look for sessions of backup jobs run by Veeam Agent operating in a standalone mode by session names.

|  |
| --- |
| Get-VBREPSession [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns sessions of backup jobs run by Veeam Agent operating in a standalone mode.

You can get all jobs sessions or search for instances directly by name. Use an appropriate parameter set for each case.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of job names. The cmdlet will return jobs with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Sessions of Backup Jobs Run by Veeam Agent in Standalone Mode

|  |  |
| --- | --- |
| This command returns all sessions of backup jobs run by Veeam Agent operating in a standalone mode.  |  | | --- | | Get-VBREPSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Session of Backup Job Run by Veeam Agent in Standalone Mode

|  |  |
| --- | --- |
| This command gets a specific session of a backup job run by Veeam Agent operating in a standalone mode.  |  | | --- | | Get-VBREPSession -Name "Backup Job Mediaserver" | |

Page updated 1/5/2024

Page content applies to build 13.0.1.1071

---
title: "Get-VBRPluginBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrpluginbackupsession_standalone.html"
last_updated: "5/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRPluginBackupSession


Short Description

Returns sessions of application backup policies and backup jobs for standalone Veeam Plug-ins.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all sessions of application backup policies and backup jobs for standalone Veeam Plug-ins.

|  |
| --- |
| Get-VBRPluginBackupSession [-MaxResults <Int32>]  [<CommonParameters>] |

* Get an array of sessions by the session name.

|  |
| --- |
| Get-VBRPluginBackupSession [-Name <string[]>] [-MaxResults <Int32>]  [<CommonParameters>] |

* Get an array of sessions by the session ID.

|  |
| --- |
| Get-VBRPluginBackupSession [-Id <guid[]>] [-MaxResults <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns sessions of application backup policies and backup jobs for standalone Veeam Plug-ins.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of names. The cmdlet will return the sessions with these names. | String[] | False | Named | False |
| Id | Specifies the array of IDs. The cmdlet will return the sessions with these IDs. | Guid[] | False | Named | False |
| MaxResults | Specifies a number of returned sessions.  Default: 500 sessions.  Note: If the MaxResults parameter value is 0, the cmdlet will return all sessions. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRPluginBackupSession](vbrpluginbackupsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Sessions

|  |  |
| --- | --- |
| This command returns all sessions of application backup policies and backup jobs for standalone Veeam Plug-ins.  |  | | --- | | Get-VBRPluginBackupSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Sessions by Name

|  |  |
| --- | --- |
| This command returns the Oracle RMAN backup session.  |  | | --- | | Get-VBRPluginBackupSession -Name "Oracle RMAN backup" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Sessions by ID

|  |  |
| --- | --- |
| This command returns the 483699a2-3fa2-45ed-86cb-230b9009b29d session.  |  | | --- | | Get-VBRPluginBackupSession -Id "483699a2-3fa2-45ed-86cb-230b9009b29d" | |



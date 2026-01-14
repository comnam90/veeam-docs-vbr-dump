---
title: "Get-VBRPluginJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrpluginjob_standalone.html"
last_updated: "8/17/2023"
product_version: "13.0.1.1071"
---

# Get-VBRPluginJob

In this article

Short Description

Returns backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRPluginJob [-Name <string>] [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRPluginBackupJob and VBRPluginBackupCopyJob objects that contains settings of the following types of jobs:

* A backup job that was created with standalone Veeam Plug-in.
* A backup copy job of a backup created with Veeam Plug-in.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of a job. The cmdlet will return the job with this name. | String | False | Named | False |
| Id | Specifies an ID of a job. The cmdlet will return the job with this ID. | Guid | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPluginBackupJob and VBRPluginBackupCopyJob objects that contain settings for plug-in backup jobs and plug-in backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Jobs

|  |  |
| --- | --- |
| This command returns all backup jobs that were created with standalone Veeam Plug-in and backup copy jobs of backups created with Veeam Plug-in that are available in the Veeam Backup & Replication infrastructure.  |  | | --- | | Get-VBRPluginJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Job by Name

|  |  |
| --- | --- |
| This command returns the plug-in backup 17 job that was created with standalone Veeam Plug-in.  |  | | --- | | Get-VBRPluginJob -Name "Plug-in backup 17" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Job by ID

|  |  |
| --- | --- |
| This command returns the 35d7b6cc-5726-4ec9-a954-f58109f3ff28 job that was created with standalone Veeam Plug-in.  |  | | --- | | Get-VBRPluginJob -Id "35d7b6cc-5726-4ec9-a954-f58109f3ff28" | |

Page updated 8/17/2023

Page content applies to build 13.0.1.1071

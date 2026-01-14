---
title: "Get-VSBJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vsbjob.html"
last_updated: "2/26/2024"
product_version: "13.0.1.1071"
---

# Get-VSBJob (obsolete)

In this article

Short Description

Returns SureBackup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VSBJob [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing SureBackup jobs.

You can get the list of all SureBackup jobs or look for specific jobs directly by name.

Run the [Get-VSBSession](get-vsbsession.md) or [Get-VSBTaskSession](get-vsbtasksession.md) cmdlet to get the information on SureBackup session or session tasks.

Run the [Get-VBRJob](get-vbrjob.md) cmdlet to look for backup, replication or copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of SureBackup job names. The cmdlet will return jobs with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Created SureBackup Jobs

|  |  |
| --- | --- |
| This command looks for the list of all created SureBackup jobs.  |  | | --- | | Get-VSBJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Specific SureBackup Jobs by Name

|  |  |
| --- | --- |
| This command looks for the SureJob 01 and SureJob 02 SureBackup jobs.  |  | | --- | | Get-VSBJob -Name "SureJob 01", "SureJob 02" | |

Page updated 2/26/2024

Page content applies to build 13.0.1.1071

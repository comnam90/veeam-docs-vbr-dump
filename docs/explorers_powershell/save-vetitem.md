---
title: "Save-VETItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/save-vetitem.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Save-VETItem


Short Description

Saves Microsoft Teams items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Save a Microsoft Teams channel post.

|  |
| --- |
| Save-VETItem [-Post] <VETPost[]> [-Path] <String> [-Force] [<CommonParameters>] |

* Save a file published in a Microsoft Teams team channel.

|  |
| --- |
| Save-VETItem [-File] <VETFile[]> [-Path] <String> [-AsZip] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet saves Microsoft Teams items such as posts and files.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Post | Specifies Microsoft Teams team channel posts that you want to save. | Accepts the [VETPost](vetpost.md)[] object. To get this object, run the [Get-VETPost](get-vetpost.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies a path to a folder where you want to save the specified posts or files.  If you want to save files as a ZIP archive, specify a path to the ZIP archive file. | String | True | 1 | False |
| Force | Defines that the cmdlet will create a folder in the specified path if the folder does not exist yet.  Default: False | SwitchParameter | False | Named | False |
| File | Specifies Microsoft Teams team channel files that you want to save. | Accepts the [VETFile](vetfile.md)[] object. To get this object, run the [Get-VETFile](get-vetfile.md) cmdlet. | True | 0 | True (ByValue) |
| AsZip | Defines that the cmdlet will save the specified files as a ZIP archive.  Default: False | SwitchParameter | False | 2 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Saving Microsoft Teams Post

|  |  |
| --- | --- |
| This example shows how to save the Announcement post to the C:\save path.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $post = Get-VETPost -Organization $org -Query "subject: announcement"  Save-VETItem -Post $post -Path "C:\save" |  Perform the following steps:   1. Get the Microsoft Teams post:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETPost](get-vetpost.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $post variable.  1. Run the Save-VETItem cmdlet. Set the $post variable as the Post parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Saving Microsoft Teams File

|  |  |
| --- | --- |
| This example shows how to save the report.txt file to the C:\save path.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $file = Get-VETFile -Organization $org -Query "filename: report"  Save-VETItem -File $file -Path "C:\save" |  Perform the following steps:   1. Get the Microsoft Teams file.  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETFile](get-vetfile.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $file variable.  1. Run the Save-VETItem cmdlet. Set the $file variable as the File parameter value. Specify the Path parameter value. |

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETPost](get-vetpost.md)
* [Get-VETFile](get-vetfile.md)



---
title: "send-vetitem"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/send-vetitem.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Sends Microsoft Teams items as email attachments.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Send a Microsoft Teams channel post.

|  |
| --- |
| Send-VETItem -To <String> [-From <String>] [-Subject <String>] [-Body <String>] [-Post] <VETPost[]> [<CommonParameters>] |

* Send a file published in a Microsoft Teams team channel.

|  |
| --- |
| Send-VETItem -To <String> [-From <String>] [-Subject <String>] [-Body <String>] [-File] <VETFile[]> [<CommonParameters>] |

Detailed Description

This cmdlet sends Microsoft Teams items as attachments in an email message.

|  |
| --- |
| Note |
| Before sending Microsoft Teams items, you must perform the following actions:   * Specify email settings for Veeam Explorer for Microsoft Teams. For more information on how to specify email settings, see [Set-VETMailSettings](set-vetmailsettings.md). * Start a restore session. For more information on how to start a restore session, see [Start-VBOTeamsItemRestoreSession](start-vboteamsitemrestoresession.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| To | Specifies an email address to which Veeam Explorer for Microsoft Teams will send Microsoft Teams items. | String | True | Named | False |
| From | Specifies an email address from which Veeam Explorer for Microsoft Teams will send Microsoft Teams items.  If this parameter is omitted, Veeam Explorer for Microsoft Teams will use the email address specified in email settings. | String | False | Named | False |
| Subject | Specifies a subject of an email message. | String | False | Named | False |
| Body | Specifies a body of an email message. | String | False | Named | False |
| Post | Specifies Microsoft Teams team channel posts. The cmdlet will send posts in the email message. | Accepts the [VETPost](vetpost.md)[] object. To get this object, run the [Get-VETPost](get-vetpost.md) cmdlet. | True | 0 | True (ByValue) |
| File | Specifies Microsoft Teams team channel files. The cmdlet will send these files in the email message. | Accepts the [VETFile](vetfile.md)[] object. To get this object, run the [Get-VETFile](get-vetfile.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Sending Microsoft Teams Post

|  |  |
| --- | --- |
| This example shows how to send the Announcement post to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $post = Get-VETPost -Organization $org -Query "subject: announcement"  Send-VETItem -Post $post -To administrator@test.local |  Perform the following steps:   1. Get the Microsoft Teams post:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETPost](get-vetpost.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $post variable.  1. Run the Send-VETItem cmdlet. Set the $post variable as the Post parameter value. Specify the To parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Sending Microsoft Teams File

|  |  |
| --- | --- |
| This example shows how to send the report.txt file to the administrator@test.local mailbox.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $file = Get-VETFile -Organization $org -Query "filename: report"  Send-VETItem -File $file -To administrator@test.local |  Perform the following steps:   1. Get the Microsoft Teams file:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETFile](get-vetfile.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $file variable.  1. Run the Send-VETItem cmdlet. Set the $file variable as the File parameter value. Specify the To parameter value. |

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETPost](get-vetpost.md)
* [Get-VETFile](get-vetfile.md)

Page updated 7/11/2025

Page content applies to build 13.0.1.1071

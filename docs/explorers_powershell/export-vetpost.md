---
title: "Export-VETPost"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-vetpost.html"
last_updated: "7/18/2025"
product_version: "13.0.1.1071"
---

# Export-VETPost


Short Description

Exports Microsoft Teams team channel posts to a file in the HTML format.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export specified posts.

|  |
| --- |
| Export-VETPost [-Post] <VETPost[]> [-Path] <String> [-Force] [<CommonParameters>] |

* Export posts of a specified channel.

|  |
| --- |
| Export-VETPost [-Channel] <VETChannel> [-Path] <String> [-From] <DateTime> [[-To] <DateTime>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet exports posts published in Microsoft Teams team channels to a file in the HTML format.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Post | Specifies Microsoft Teams team channel posts that you want to export. | Accepts the [VETPost](vetpost.md)[] object. To get this object, run the [Get-VETPost](get-vetpost.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies a path to the folder and a name for the HTML file where you want to export posts. | String | True | 1 | False |
| Force | Defines that the cmdlet will create a folder where to save the HTML file if the specified folder does not exist.  Default: False | SwitchParameter | False | Named | False |
| Channel | Specifies a Microsoft Teams team channel. The cmdlet will export posts from this channel. | Accepts the [VETChannel](vetchannel.md) object. To get this object, run the [Get-VETChannel](get-vetchannel.md) cmdlet. | True | 0 | True (ByValue) |
| From | Specifies the point in time that defines the start of the period for which you want to export posts.  The cmdlet will export posts created within the specified time period. | DateTime | True | 2 | False |
| To | Specifies the point in time that defines the end of the period for which you want to export posts.  The cmdlet will export posts created within the specified time period. | DateTime | False | 3 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Specified Posts

|  |  |
| --- | --- |
| This example shows how to export specified posts. The cmdlet will export posts with the following settings:   * The cmdlet will export posts from channels of the IT team that contain the announcement keyword. * The cmdlet will export posts to the announcements.html file.   |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $post = Get-VETPost -team $team -Query "subject: announcement"  Export-VETPost -Post $post -Path "C:\export\announcements.html" |  Perform the following steps:   1. Get posts that contain the announcement keyword:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETPost](get-vetpost.md) cmdlet. Set the $team variable as the Team parameter value. Specify the Query parameter value. Save the result to the $post variable.  1. Run the Export-VETPost cmdlet. Set the $post variable as the Post parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Posts of Specified Channel

|  |  |
| --- | --- |
| This example shows how to export posts of the specified channel. The cmdlet will export posts with the following settings:   * The cmdlet will export posts from the General channel of the IT team. * The cmdlet will export posts published between 7/1/2023 10:00 AM and 8/31/2023 10:00 AM to the posts.html file.   |  | | --- | | $datefrom = [datetime]"7/1/2023 10:00 AM"  $dateto = [datetime]"8/31/2023 10:00 AM"  $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  Export-VETPost -Channel $channel -Path "C:\export\posts.html" -From $datefrom -To $dateto |  Perform the following steps:   1. Convert the time that defines the start of the period for which you want to export posts to the DateTime format. Save the result to the $datefrom variable. 2. Convert the time that defines the end of the period for which you want to export posts to the DateTime format. Save the result to the $dateto variable. 3. Get the General channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the Export-VETPost cmdlet. Set the $channel variable as the Channel parameter value. Specify the Path parameter value. Set the $datefrom variable as the From parameter value. Set the $dateto variable as the To parameter value. |

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)
* [Get-VETChannel](get-vetchannel.md)
* [Get-VETPost](get-vetpost.md)



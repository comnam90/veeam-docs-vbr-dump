---
title: "Examples of Use"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/examples_of_use.html"
last_updated: "2/28/2025"
product_version: "13.0.1.1071"
---


In this article

This section describes how to use a PowerShell script to export Teams channel posts published in a specific time frame to the machine where the PowerShell session is running.

To export Microsoft Teams channel posts, use the [Export-VETPost](export-vetpost.md) cmdlet. This cmdlet includes two parameter sets: a parameter set to export specific posts, and a parameter set to export posts of a specified channel. This example uses the second parameter set.

To perform this export operation, specify the following settings:

* Microsoft Teams channel — to specify the channel whose posts you want to export.
* Time range of the posts — to specify the posts that you want to export.

The cmdlet treats these settings as objects. We will get these objects and save them to variables:

1. To specify the Microsoft Teams channel, do the following:

1. Get a Veeam Explorer for Microsoft Teams restore session.

* If this is a fresh PowerShell environment, you must first start a Veeam Explorer for Microsoft Teams restore session. This example uses the remote session method, which works with Veeam Explorer for Microsoft Teams that comes with both Veeam Backup & Replication and Veeam Backup for Microsoft 365 installations. The machine where the PowerShell session is running will connect to the Veeam Backup for Microsoft 365 server that created the backup.

To provide the connection credentials, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $backupservercreds variable.

|  |
| --- |
| $backupservercreds = Get-Credential |

Run the [Start-VBOTeamsItemRestoreSession](start-vboteamsitemrestoresession.md) cmdlet to start a Veeam Explorer for Microsoft Teams restore session. Specify the DNS name or IP address of the Veeam Backup for Microsoft 365 backup server as the Server parameter value. Set the $backupservercreds variable as the Credential parameter value. Save the result to the $session variable.

|  |
| --- |
| $session = Start-VBOTeamsItemRestoreSession -Server "srv96.tech.local" -Credential $backupservercreds |

* If you already have a restore session started with the necessary restore point, just run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet to get an array of active restore sessions. If you have multiple active restore sessions, specify the position of the necessary restore session in the array of returned sessions. This example uses the first restore session in the array. Save the result to the $session variable.

|  |
| --- |
| $session = (Get-VBOTeamsItemRestoreSession)[0] |

1. Get a Microsoft Teams organization. To do this, run the [Get-VETOrganization](get-vetorganization.md) cmdlet. If there are multiple organizations in the restore session, specify the position of the necessary organization in the array of returned organizations, or specify the organization name as the Name parameter value. This example uses the second approach. Save the result to the $org variable.

|  |
| --- |
| $org = Get-VETOrganization -Session $session -Name "ABCCompany" |

1. Get a Microsoft Teams team. To do this, run the [Get-VETTeam](get-vetteam.md) cmdlet. Specify the $org variable as the Organization parameter value. If there are multiple teams in the organization, specify the position of the necessary team in the array of returned teams, or specify the team name as the DisplayName parameter value. This example uses the second approach. Save the result to the $team variable.

|  |
| --- |
| $team = Get-VETTeam -Organization $org -DisplayName "IT" |

1. Get a Microsoft Teams channel. To do this, run the [Get-VETChannel](get-vetchannel.md) cmdlet. Specify the $team variable as the Team parameter value. If there are multiple channels in the team, specify the position of the necessary channel in the array of returned channels, or specify the channel name as the DisplayName parameter value. This example uses the second approach. Save the result to the $channel variable.

|  |
| --- |
| $channel = Get-VETChannel -Team $team -DisplayName "General" |

1. Get the time range of the necessary posts. To do this, do the following:

1. Specify the time that defines the start of the period for which you want to export posts and convert it to the DateTime format. Save the result to the $datefrom variable.

|  |
| --- |
| $datefrom = [datetime]"2/16/2025 10:00 AM" |

1. Specify the time that defines the end of the period for which you want to export posts and convert it to the DateTime format. Save the result to the $dateto variable.

|  |
| --- |
| $dateto = [datetime]"3/15/2025 2:00 PM" |

1. Run the [Export-VETPost](export-vetpost.md) cmdlet to initiate the restore process. Set the $channel variable as the Channel parameter value. Set the $datefrom variable as the From parameter value. Set the $dateto variable as the To parameter value. Specify the path to the exported file on the machine where the PowerShell session is running.

|  |
| --- |
| Export-VETPost -Channel $channel -Path "C:\export\posts.html" -From $datefrom -To $dateto |

Page updated 2/28/2025

Page content applies to build 13.0.1.1071

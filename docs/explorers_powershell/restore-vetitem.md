---
title: "Restore-VETItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-vetitem.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Restore-VETItem


Short Description

Restores Microsoft Teams items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore posts of a Microsoft Teams channel for a specified time period.

|  |
| --- |
| Restore-VETItem -Credential <PSCredential> [-Channel] <VETChannel> -PostsFrom <DateTime> [-PostsTo <DateTime>] [<CommonParameters>] |

* Restore all posts of a Microsoft Teams channel.

|  |
| --- |
| Restore-VETItem -Credential <PSCredential> [-Channel] <VETChannel> [-AllPosts] [<CommonParameters>] |

* Restore files of a Microsoft Teams channel.

|  |
| --- |
| Restore-VETItem -Credential <PSCredential> [-RestoreChangedItem] [-RestoreMissingItem] [-File] <VETFile[]> [-RestoreOnlyLatestVersion] [<CommonParameters>] |

* Restore tabs of a Microsoft Teams channel.

|  |
| --- |
| Restore-VETItem -Credential <PSCredential> [-RestoreChangedItem] [-RestoreMissingItem] [-Tab] <VETOtherTab[]> [<CommonParameters>] |

* Restore a Microsoft Teams channel.

|  |
| --- |
| Restore-VETItem -Credential <PSCredential> [-Channel] <VETChannel> [-RestoreChangedItem] [-RestoreMissingItem] [-RestoreMembers] [<CommonParameters>] |

* Restore a Microsoft Teams team.

|  |
| --- |
| Restore-VETItem -Credential <PSCredential> [-RestoreChangedItem] [-RestoreMissingItem] [-Team] <VETTeam> [-RestoreMembers] [-RestoreSettings] [<CommonParameters>] |

* Restore multiple Microsoft Teams teams.

|  |
| --- |
| Restore-VETItem -Credential <PSCredential> [-RestoreChangedItem] [-RestoreMissingItem] [-MultipleTeams] <VETTeam[]> [-RestoreMembers] [-RestoreSettings] [<CommonParameters>] |

* Restore all posts of a Microsoft Teams channel using multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> -ApplicationCertificatePath <String> -ApplicationCertificatePassword <SecureString> [-Channel] <VETChannel> [-AllPosts] [<CommonParameters>] |

* Restore all posts of a Microsoft Teams channel using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> [-Channel] <VETChannel> [-AllPosts] [<CommonParameters>] |

* Restore posts of a Microsoft Teams channel for a specified time period using multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> -ApplicationCertificatePath <String> -ApplicationCertificatePassword <SecureString> [-Channel] <VETChannel> -PostsFrom <DateTime> [-PostsTo <DateTime>] [<CommonParameters>] |

* Restore posts of a Microsoft Teams channel for a specified time period using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> [-Channel] <VETChannel> -PostsFrom <DateTime> [-PostsTo <DateTime>] [<CommonParameters>] |

* Restore files using multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> -ApplicationCertificatePath <String> -ApplicationCertificatePassword <SecureString> [-RestoreChangedItem] [-RestoreMissingItem] [-File] <VETFile[]> [-RestoreOnlyLatestVersion] [<CommonParameters>] |

* Restore files using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> [-RestoreChangedItem] [-RestoreMissingItem] [-File] <VETFile[]> [-RestoreOnlyLatestVersion] [<CommonParameters>] |

* Restore tabs using multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> -ApplicationCertificatePath <String> -ApplicationCertificatePassword <SecureString> [-RestoreChangedItem] [-RestoreMissingItem] [-Tab] <VETOtherTab[]> [<CommonParameters>] |

* Restore tabs using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> [-RestoreChangedItem] [-RestoreMissingItem] [-Tab] <VETOtherTab[]> [<CommonParameters>] |

* Restore a channel using multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> -ApplicationCertificatePath <String> -ApplicationCertificatePassword <SecureString> [-Channel] <VETChannel> [-RestoreChangedItem] [-RestoreMissingItem] [-RestoreMembers] [<CommonParameters>] |

* Restore a channel using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> [-Channel] <VETChannel> [-RestoreChangedItem] [-RestoreMissingItem] [-RestoreMembers] [<CommonParameters>] |

* Restore a team using multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> -ApplicationCertificatePath <String> -ApplicationCertificatePassword <SecureString> [-RestoreChangedItem] [-RestoreMissingItem] [-Team] <VETTeam> [-ImpersonationAccountName <String>] [-RestoreMembers] [-RestoreSettings] [<CommonParameters>] |

* Restore a team using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> [-RestoreChangedItem] [-RestoreMissingItem] [-Team] <VETTeam> [-RestoreMembers] [-RestoreSettings] [<CommonParameters>] |

* Restore multiple teams using multi-factor authentication with a Microsoft Entra application.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> -ApplicationCertificatePath <String> -ApplicationCertificatePassword <SecureString> [-RestoreChangedItem] [-RestoreMissingItem] [-MultipleTeams] <VETTeam[]> [-ImpersonationAccountName <String>] [-RestoreMembers] [-RestoreSettings] [<CommonParameters>] |

* Restore multiple teams using multi-factor authentication with a Microsoft Entra application ID.

|  |
| --- |
| Restore-VETItem -ApplicationId <Guid> [-RestoreChangedItem] [-RestoreMissingItem] [-MultipleTeams] <VETTeam[]> [-RestoreMembers] [-RestoreSettings] [<CommonParameters>] |

Detailed Description

This cmdlet allows you to restore Microsoft Teams items:

* Teams
* Channels
* Posts
* Files
* Tabs

You can restore Microsoft Teams items with one of the following authentication methods:

* Authentication methods that utilize legacy protocols.
* Multi-factor authentication. To restore data, the cmdlet utilizes a Microsoft Entra application.

|  |
| --- |
| Note: |
| To perform restore operations, you must first start a restore session. For more information on how to start a restore session, see [Start-VBOTeamsItemRestoreSession](start-vboteamsitemrestoresession.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credential | Specifies credentials that will be used for authenticating to the Microsoft 365 organization. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |
| Channel | Specifies a Microsoft Teams team channel. The cmdlet will restore items of this channel. | Accepts the [VETChannel](vetchannel.md) object. To get this object, run the [Get-VETChannel](get-vetchannel.md) cmdlet. | True | 0 | True (ByValue) |
| PostsFrom | Specifies the point in time that defines the start of the period for which you want to restore posts of a Microsoft Teams channel.  The cmdlet will restore posts published within the specified time period. The time when a post was published is defined by the last modification time of the post.  Note: If you use this parameter, you cannot use the AllPosts parameter. | DateTime | True | Named | False |
| PostsTo | Specifies the point in time that defines the end of the period for which you want to restore posts of a Microsoft Teams channel.  The cmdlet will restore posts publish within the specified time period. The time when a post was published is defined by the last modification time of the post.  Note: If you use this parameter, you cannot use the AllPosts parameter. | DateTime | False | Named | False |
| AllPosts | Defines that the cmdlet will restore all posts of a Microsoft Teams channel.  Default: False  Note: If you use this parameter, you cannot use the PostsFrom and PostsTo parameters. | SwitchParameter | True | Named | False |
| RestoreChangedItem | Defines that the cmdlet will restore items that have changed in the original location since the time when the backup was created.  Default: False | SwitchParameter | False | Named | False |
| RestoreMissingItem | Defines that the cmdlet will restore items that are missing in the original location.  Default: False | SwitchParameter | False | Named | False |
| File | Specifies Microsoft Teams team channel files. The cmdlet will restore the specified files. | Accepts the [VETFile](vetfile.md)[] object. To get this object, run the [Get-VETFile](get-vetfile.md) cmdlet. | True | 0 | True (ByValue) |
| RestoreOnlyLatestVersion | Defines that the cmdlet will restore only the latest version of a backed-up file.  If you do not use this parameter, Veeam Explorer for Microsoft Teams will restore all versions of a file from the backup.  Default: False | SwitchParameter | False | Named | False |
| Tab | Specifies Microsoft Teams channel tabs. The cmdlet will restore the specified tabs. | Accepts the [VETOtherTab](vetothertab.md)[] object. To get this object, run the [Get-VETOtherTab](get-vetothertab.md) cmdlet. | True | 0 | True (ByValue) |
| RestoreMembers | Defines that the cmdlet will restore team members of the specified team along with their roles.  Default: False | SwitchParameter | False | Named | False |
| Team | Specifies Microsoft Teams team. The cmdlet will restore items of this team. | Accepts the [VETTeam](vetteam.md) object. To get this object, run the [Get-VETTeam](get-vetteam.md) cmdlet. | True | 0 | True (ByValue) |
| RestoreSettings | Defines that the cmdlet will restore settings of the specified team.  Default: False | SwitchParameter | False | Named | False |
| MultipleTeams | Specifies Microsoft Teams teams. The cmdlet will restore items of these teams. | Accepts the [VETTeam](vetteam.md)[] object. To get this object, run the [Get-VETTeam](get-vetteam.md) cmdlet. | True | 0 | True (ByValue) |
| ApplicationId | To restore data using multi-factor authentication.  Specifies a Microsoft Entra application ID. The cmdlet will use this application ID to set up a secure connection to a Microsoft organization. | Guid | True | Named | False |
| ApplicationCertificatePath | To restore data using multi-factor authentication.  Specifies a path to the certificate. The cmdlet will import this certificate that is located in this path to set up an encrypted connection to a Microsoft organization. | String | True | Named | False |
| ApplicationCertificatePassword | To restore data using multi-factor authentication.  Specifies the certificate password. The cmdlet will use this password to confirm the certificate that you want to import to a Microsoft Entra application. | SecureString | True | Named | False |
| ImpersonationAccountName | To restore data using multi-factor authentication.  Specifies a user name of the account that will be used as a team owner account to restore a team. This may be useful if you restore a previously removed team at the time when the original team owner account does not exist in Microsoft 365. Use this parameter together with the ApplicationCertificatePassword parameter.  If you omit this parameter, the cmdlet will restore a team using an original team owner account from the backup. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Microsoft Teams Posts

|  |  |
| --- | --- |
| This example shows how to restore posts of the General Microsoft Teams team channel created between 7/1/2023 10:00 AM and 8/31/2023 10:00 AM.  |  | | --- | | $credentials = Get-Credential  $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  Restore-VETItem -Credential $credentials -Channel $channel -PostsFrom "7/1/2023 10:00 AM" -PostsTo "8/31/2023 10:00 AM" |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type credentials that you want to use for connecting to the Microsoft 365 organization. Save the result to the $credentials variable. 2. Get the Microsoft Teams channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the Restore-VETItem cmdlet. Set the $credentials variable as the Credential parameter value. Set the $channel variable as the Channel parameter value. Specify the From and To parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Microsoft Teams Channel

|  |  |
| --- | --- |
| This example shows how to restore the General Microsoft Teams team channel with the following settings:   * The cmdlet will restore changed items. * The cmdlet will restore missing items.   |  | | --- | | $credentials = Get-Credential  $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  Restore-VETItem -Credential $credentials -Channel $channel -RestoreChangedItem -RestoreMissingItem |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type credentials that you want to use for connecting to the Microsoft 365 organization. Save the result to the $credentials variable. 2. Get the Microsoft Teams channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the Restore-VETItem cmdlet. Specify the following settings:  * Set the $credentials variable as the Credential parameter value. * Set the $channel variable as the Channel parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreMissingItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Microsoft Teams Files

|  |  |
| --- | --- |
| This example shows how to restore files of a Microsoft Teams team channel with the following settings:   * The cmdlet will restore files whose names contain the report keyword. * The cmdlet will restore changed items. * The cmdlet will restore missing items.   |  | | --- | | $credentials = Get-Credential  $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  $file = Get-VETFile -Channel $channel -Query "filename: report"  Restore-VETItem -Credential $credentials -File $file -RestoreChangedItem -RestoreMissingItem |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type credentials that you want to use for connecting to the Microsoft 365 organization. Save the result to the $credentials variable. 2. Get the files:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable. 5. Run the [Get-VETFile](get-vetfile.md) cmdlet. Set the $channel variable as the Channel parameter value. Specify the Query parameter value. Save the result to the $file variable.  1. Run the Restore-VETItem cmdlet. Specify the following settings:  * Set the $credentials variable as the Credential parameter value. * Set the $file variable as the File parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreMissingItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Microsoft Teams Channel Tab

|  |  |
| --- | --- |
| This example shows how to restore the Website Microsoft Teams team channel tab with the following settings:   * The cmdlet will restore changed items. * The cmdlet will restore missing items.   |  | | --- | | $credentials = Get-Credential  $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  $tab = Get-VETOtherTab -Channel $channel -Query "name: website"  Restore-VETItem -Credential $credentials -Tab $tab -RestoreChangedItem -RestoreMissingItem |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type credentials that you want to use for connecting to the Microsoft 365 organization. Save the result to the $credentials variable. 2. Get the Microsoft Teams channel tab:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable. 5. Run the [Get-VETOtherTab](get-vetothertab.md) cmdlet. Set the $channel variable as the Channel parameter value. Specify the Query parameter value. Save the result to the $tab variable.  1. Run the Restore-VETItem cmdlet. Specify the following settings:  * Set the $credentials variable as the Credential parameter value. * Set the $tab variable as the Tab parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreMissingItem parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Restoring Microsoft Teams Team

|  |  |
| --- | --- |
| This example shows how to restore the IT Microsoft Teams team with the following settings:   * The cmdlet will restore changed items. * The cmdlet will restore missing items. * The cmdlet will restore team members. * The cmdlet will restore team settings.   |  | | --- | | $credentials = Get-Credential  $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  Restore-VETItem -Credential $credentials -Team $team -RestoreChangedItem -RestoreMissingItem -RestoreMembers -RestoreSettings |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type credentials that you want to use for connecting to the Microsoft 365 organization. Save the result to the $credentials variable. 2. Get the Microsoft Teams team:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable.  1. Run the Restore-VETItem cmdlet. Specify the following settings:  * Set the $credentials variable as the Credential parameter value. * Set the $team variable as the Team parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreMissingItem parameter. * Provide the RestoreMembers parameter. * Provide the RestoreSettings parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Restoring Microsoft Teams Channel Using Multi-Factor Authentication with Microsoft Entra Application ID

|  |  |
| --- | --- |
| This example shows how to restore the General Microsoft Teams team channel with the following settings:   * The cmdlet will use the c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 Microsoft Entra application ID.  * The cmdlet will restore changed items. * The cmdlet will restore missing items.   |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  Restore-VETItem -ApplicationId c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 -Channel $channel -RestoreChangedItem -RestoreMissingItem |  Perform the following steps:   1. Get the Microsoft Teams channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the Restore-VETItem cmdlet. Specify the following settings:  * Specify the ApplicationId parameter value. * Set the $channel variable as the Channel parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreMissingItem parameter.  1. To set up a secure connection to a Microsoft organization, open the <https://microsoft.com/devicelogin> link in a browser and enter the code that you get in the PowerShell Console for authenticating to the Microsoft 365 server. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Restoring Microsoft Teams Channel Using Multi-Factor Authentication with Microsoft Entra Application Certificate

|  |  |
| --- | --- |
| This example shows how to restore the General Microsoft Teams team channel with the following settings:   * The cmdlet will use the c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 Microsoft Entra application ID. * The cmdlet will use the certificate located at the C:\Certificate path.  * The cmdlet will restore changed items. * The cmdlet will restore missing items.   |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  Enter password: \*\*\*\*\*\*\*\*  Restore-VETItem -ApplicationId c276f9ce-e4f2-4bdf-b9f2-e6c311c2e2a5 -ApplicationCertificatePath "C:\Certificate\Cert.pfx" -ApplicationCertificatePassword $securepassword -Channel $channel -RestoreChangedItem -RestoreMissingItem |  Perform the following steps:   1. Get the Microsoft Teams channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet to specify the password. Specify the text that will show up in the password prompt window in the Prompt parameter. Specify the AsSecureString parameter to convert the password to a secure string. 2. Enter the password. 3. Run the Restore-VETItem cmdlet. Specify the following settings:  * Specify the ApplicationId parameter value. * Specify the ApplicationCertificatePath parameter value. * Set the $securepassword variable as the ApplicationCertificatePassword parameter value. * Set the $channel variable as the Channel parameter value. * Provide the RestoreChangedItem parameter. * Provide the RestoreMissingItem parameter. |

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)

* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)
* [Get-VETChannel](get-vetchannel.md)
* [Get-VETFile](get-vetfile.md)
* [Get-VETOtherTab](get-vetothertab.md)



---
title: "Start-VBOExchangeItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vboexchangeitemrestoresession.html"
last_updated: "7/24/2025"
product_version: "13.0.1.1071"
---

# Start-VBOExchangeItemRestoreSession


Short Description

Starts restore sessions to explore backed-up Microsoft Exchange items and to perform operations with these items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Explore or restore Microsoft Exchange objects from the latest restore point.

|  |
| --- |
| Start-VBOExchangeItemRestoreSession [-LatestState] [-Job <IVBOJob>] [-Organization <IVBOOrganization>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

* Explore or restore Microsoft Exchange objects from the specified restore point.

|  |
| --- |
| Start-VBOExchangeItemRestoreSession -RestorePoint <IVBORestorePoint> [-Job <IVBOJob>] [-Organization <IVBOOrganization>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

* Explore or restore Microsoft Exchange objects from the latest restore point remotely.

|  |
| --- |
| Start-VBOExchangeItemRestoreSession -Server <String> -Credential <PSCredential> [-Port <Int32>] [-SkipCertificateCheck] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

Detailed Description

This cmdlet establishes a connection to the Veeam Backup for Microsoft 365 server and retrieves Exchange items backed up on this server. Within the restore session, you can get backed-up Exchange objects using the following cmdlets:

* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Get-VEXFolder](get-vexfolder.md)
* [Get-VEXItem](get-vexitem.md)

After you get backed-up Exchange objects, you can perform the following operations with these objects:

* [Export-VEXItem](export-vexitem.md)
* [Restore-VEXItem](restore-vexitem.md)
* [Send-VEXItem](send-vexitem.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LatestState | Defines that the cmdlet will retrieve data from a mailbox database at the state of the latest restore point.  Default: False | SwitchParameter | True | Named | False |
| Job | Specifies a backup job to start a new restore session. You will be able to use the session to perform operations with items backed up by this job. | Accepts the IVBOJob object. To get this object, run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. | False | Named | True (ByValue) |
| Organization | Specifies an organization to start a new restore session. You will be able to use the session to perform operations with items backed up for this organization. | Accepts the IVBOOrganization object. To get this object, run the [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. | False | Named | True (ByValue) |
| ShowDeleted | Defines that deleted items will be included in the current session. If you provide this parameter, you will be able to perform operations with these items.  Note: If you provide this parameter, the amount of data returned by cmdlets within the current session may significantly increase.  Default: False | SwitchParameter | False | Named | False |
| ShowAllVersions | Defines that all versions of backed-up items will be included in the current session. If you provide this parameter, you will be able to perform operations with these items.  Note: If you provide this parameter, the amount of data returned by cmdlets within the current session may significantly increase.  Default: False | SwitchParameter | False | Named | False |
| Reason | Specifies a reason to perform restore operation. | String | False | Named | False |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with items that this restore point contains. | Accepts the IVBORestorePoint object. To get this object, run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. | True | Named | True (ByValue) |
| Server | Specifies DNS name or IP address of the Veeam Backup for Microsoft 365 server that backed up items that you want to restore. | String | True | Named | False |
| Credential | Specifies credentials that will be used for authenticating to the Veeam Backup for Microsoft 365 server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |
| Port | Specifies a port number that will be used to connect to the Veeam Backup for Microsoft 365 server. | Int32 | False | Named | False |
| SkipCertificateCheck | Defines that the cmdlet will not perform the SSL certificate check.  Default: False | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOExchangeRestoreSession](vboexchangerestoresession.md) object that contains settings of the restore session started to perform operations with backed-up Microsoft Exchange items.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session from Latest Restore Point

|  |  |
| --- | --- |
| This example shows how to start a restore session to perform operations with Microsoft Exchange objects. The restore session will start with the following settings:   * The cmdlet will retrieve data from a mailbox database from the state of the latest restore point. * The cmdlet will start a restore session only for backups associated with the ABC organization.     |  | | --- | | $organization = Get-VBOOrganization -Name "ABC"  Start-VBOExchangeItemRestoreSession -LatestState -Organization $organization |  Perform the following steps:   1. Run the [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. Specify the Name parameter value. Save the result to the $organization variable. 2. Run the Start-VBOExchangeItemRestoreSession cmdlet. Provide the LatestState parameter. Set the $organization variable as the Organization parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session from Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start a restore session to perform operations with Microsoft Exchange objects. The restore session will start with the following settings:   * The cmdlet will retrieve a mailbox database at the state of the selected restore point. * The cmdlet will start a restore session only for backups that were created by the Sales Reports backup job.     |  | | --- | | $restorepoint = Get-VBORestorePoint  $job = Get-VBOJob -Name "Sales Reports"  Start-VBOExchangeItemRestoreSession -RestorePoint $restorepoint[2] -Job $job |  Perform the following steps:   1. Run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. Save the result to the $restorepoint variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the third restore session in the array.   1. Run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Start-VBOExchangeItemRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value and select the necessary restore point. In this example, it is the third restore point in the array. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Restore Session from Latest Restore Point Remotely

|  |  |
| --- | --- |
| This example shows how to start a remote restore session to perform operations with Microsoft Exchange objects. The cmdlet will connect to the vbo365server.support.local server to retrieve a mailbox database at the state of the latest restore point.  |  | | --- | | $credentials = Get-Credential  Start-VBOExchangeItemRestoreSession -Server vbo365server.support.local -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $credentials variable. 2. Run the Start-VBOExchangeItemRestoreSession cmdlet. Specify the Server parameter value. Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Performing Restore Scenario

|  |  |
| --- | --- |
| This example shows how to perform a restore scenario. The restore scenario includes the following steps:   * Start a remote restore session for a mailbox database at the state of the latest restore point. * Perform an item restore from an organization mailbox. * Stop the restore session.     |  | | --- | | $vbosrvcreds = Get-Credential  $session = Start-VBOExchangeItemRestoreSession -Server vbo365server.support.local -Credential $vbosrvcreds  $database = Get-VEXDatabase -Session $session  $mailbox = Get-VEXMailbox -Database $database[0] -Name "sales"  $exsrvcreds = Get-Credential  Restore-VEXItem -Mailbox $mailbox -Server outlook.office365.com -Credential $exsrvcreds -RestoreChangedItem  Stop-VBOExchangeItemRestoreSession -Session $session |  Perform the following steps:   1. Start the remote restore session for the mailbox database at the state of the latest restore point:  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $vbosrvcreds variable. 2. Run the Start-VBOExchangeItemRestoreSession cmdlet. Specify the Server parameter value. Set the $vbosrvcreds variable as the Credential parameter value. Save the results to the $session variable.  1. Perform an item restore:  1. Get a mailbox item that you want to restore:  1. Run the [Get-VEXDatabase](get-vexdatabase.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $database variable. 2. Run the [Get-VEXMailbox](get-vexmailbox.md) cmdlet. Set the $database variable as the Database parameter value and select the necessary database. In this example, it is the first database in the array. Specify the Name parameter value. Save the result to the $mailbox variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. Save the result to the $exsrvcreds variable. 2. Run the [Restore-VEXitem](restore-vexitem.md) cmdlet. Set the $mailbox variable as the Mailbox parameter value. Specify the Server parameter value. Set the $exsrvcreds variable as the Credential parameter value. Provide the RestoreChangedItem parameter.  1. Run the [Stop-VBOExchangeItemRestoreSession](stop-vboexchangeitemrestoresession.md) cmdlet. Set the $session variable as the Session parameter value. |

Related Commands

* [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80)
* [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80)
* [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Restore-VEXitem](restore-vexitem.md)
* [Stop-VBOExchangeItemRestoreSession](stop-vboexchangeitemrestoresession.md)



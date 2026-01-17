---
title: "Start-VBRSharePointItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vbrsharepointitemrestoresession.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Start-VBRSharePointItemRestoreSession


Short Description

Starts restore sessions to explore backed-up Microsoft SharePoint databases and to perform operations with these databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a restore session from a specific restore point of the Microsoft SharePoint database.

|  |
| --- |
| Start-VBRSharePointItemRestoreSession [-RestorePoint] <IVBRApplicationRestorePoint> [-StagingServerName <String>] [-StagingInstanceName <String>] [-StagingServerPort <Int32>] [-GuestCredential <PSCredential>] [-SqlCredential <PSCredential>] [-UseWindowsAuthentication] [<CommonParameters>] |

* Start a restore session from the restore points of backed-up machines with Microsoft SQL databases for the specified Microsoft SharePoint site collection.

|  |
| --- |
| Start-VBRSharePointItemRestoreSession [-SiteCollectionRestorePoint] <IVBRSiteCollection> [-StagingServerName <String>] [-StagingInstanceName <String>] [-StagingServerPort <Int32>] [-GuestCredential <PSCredential>] [-SqlCredential <PSCredential>] [-UseWindowsAuthentication] [<CommonParameters>] |

Detailed Description

This cmdlet allows you to start restore sessions and recover Microsoft SharePoint databases. You can run restore sessions with the following scenarios:

* Restore session of all site collections and Microsoft SharePoint databases from a specific restore point.
* Restore session of backed-up machines with Microsoft SQL databases for the specified Microsoft SharePoint site collection.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point. The cmdlet will get a Microsoft SharePoint database from the specified restore point. | Accepts the [IVBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13) object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | 0 | True (ByValue) |
| StagingServerName | Specifies a name of the staging SQL server. The cmdlet will mount the restore point of the machine with the SharePoint database to the specified server. | String | False | Named | False |
| StagingInstanceName | Specifies a name of a Microsoft SQL instance. The cmdlet will create the content database within this instance. | String | False | Named | False |
| StagingServerPort | Specifies a port number. The cmdlet will use this port to connect to the staging Microsoft SQL server. | Int32 | False | Named | False |
| GuestCredential | Specifies user account credentials to connect to the staging Microsoft SQL server. The user account must have the Full control permissions. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| SqlCredential | Specifies credentials for authenticating to the Microsoft SQL server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseWindowsAuthentication | Defines that the cmdlet will use Windows authentication.  Default: False | SwitchParameter | False | Named | False |
| SiteCollectionRestorePoint | Specifies restore points of backed-up machines with Microsoft SQL databases for the specified Microsoft SharePoint site collection. | Accepts the [IVBRSiteCollection](vbrsitecollection.md) object. To get this object, run the [Get-VBRSiteCollectionRestorePoint](get-vbrsitecollectionrestorepoint.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBRSharePointRestoreSession](vbrsharepointrestoresession.md) object that contains settings of the restore session started to explore backed-up Microsoft SharePoint databases and to perform operations with these databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session for All Site Collections

|  |  |
| --- | --- |
| This example shows how to start a restore session for all site collections and Microsoft SharePoint databases from a specific restore point.  |  | | --- | | $restorepoint = Get-VBRApplicationRestorePoint -SharePoint  Start-VBRSharePointItemRestoreSession -RestorePoint $restorepoint[0] |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the SharePoint parameter. Save the result to the $restorepoint variable. 2. Run the Start-VBRSharePointItemRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session from Microsoft SQL Backup

|  |  |
| --- | --- |
| This example shows how to start a restore session from a Microsoft SQL backup that contains the necessary Microsoft SharePoint database.  |  | | --- | | $restorepoint = Get-VBRApplicationRestorePoint -SQL  Start-VBRSharePointItemRestoreSession -RestorePoint $restorepoint[0] |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the SQL parameter. Save the result to the $restorepoint variable. 2. Run the Start-VBRSharePointItemRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Restore Session from Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start a restore session for all site collections and Microsoft SharePoint databases from a specific restore point. The cmdlet will use a staging server and will create the content database within the VEEAMSQL2016 instance.  |  | | --- | | $restorepoint = Get-VBRApplicationRestorePoint -SharePoint  $creds = Get-Credential  Start-VBRSharePointItemRestoreSession -RestorePoint $restorepoint -StagingServerName "LOCALHOST" -StagingInstanceName "VEEAMSQL2016" -GuestCredential $creds -SqlCredential $creds -UseWindowsAuthentication |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the SharePoint parameter. Save the result to the $restorepoint variable. 2. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object that you want to use for authenticating to the staging server and an SQL instance. Save the result to the $creds variable. 3. Run the Start-VBRSharePointItemRestoreSession cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the StagingServerName parameter value. * Specify the StagingInstanceName parameter value. * Set the $creds variable as the GuestCredential parameter value. * Set the $creds variable as the SqlCredential parameter value. * Provide the UseWindowsAuthentication parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Starting Restore Session from Microsoft SQL Databases with Microsoft SharePoint Site Collections

|  |  |
| --- | --- |
| This example shows how to start a restore session from the restore points of backed-up machines with Microsoft SQL databases for the SharePoint server Microsoft SharePoint site collection.  |  | | --- | | $restorepoint = Get-VBRApplicationRestorePoint -SharePoint -Name "SharePoint server"  $sitecollection = Get-VBRSiteCollection -RestorePoint $restorepoint  $sitepoint = Get-VBRSiteCollectionRestorePoint -SiteCollection $sitecollection  Start-VBRSharePointItemRestoreSession -SiteCollectionRestorePoint $sitepoint[0] |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the SharePoint parameter. Save the result to the $restorepoint variable.  1. Run the [Get-VBRSiteCollection](get-vbrsitecollection.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $sitecollection variable.  1. Run the [Get-VBRSiteCollectionRestorePoint](get-vbrsitecollectionrestorepoint.md) cmdlet. Set the $sitecollection variable as the SiteCollection parameter value. Save the result to the $sitepoint variable.  1. Run the Start-VBRSharePointItemRestoreSession cmdlet. Set the $sitepoint variable as the SiteCollectionRestorePoint parameter value. |

Related Commands

* [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

* [Get-VBRSiteCollectionRestorePoint](get-vbrsitecollectionrestorepoint.md)
* [Get-VBRSiteCollection](get-vbrsitecollection.md)



---
title: "Get-VEMDBDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbdatabase.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---

# Get-VEMDBDatabase


Short Description

Returns backed-up MongoDB databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEMDBDatabase [-Session] <VEMDBRestoreSession> [-Name <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up MongoDB databases. After you get the backed-up databases, you can use the [Get-VEMDBCollection](get-vemdbcollection.md) cmdlet to get the collections you need.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with MongoDB data. | Accepts the [VEMDBRestoreSession](vemdbrestoresession.md) object. To get this object, run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names of MongoDB databases. The cmdlet will return an array of databases with the specified names.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBDatabase](vemdbdatabase.md)[] array that contains backed-up MongoDB databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All MongoDB Databases Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get an array of all MongoDB databases within the specified restore session.  |  | | --- | | $session = Get-VEMDBRestoreSession  $databases = Get-VEMDBDatabase -Session $session[1] |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the second restore session in the array).   1. Run the Get-VEMDBDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $databases variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting MongoDB Databases with Specified Names

|  |  |
| --- | --- |
| This example shows how to get an array of MongoDB databases with the specified names.  |  | | --- | | $session = Get-VEMDBRestoreSession  $dbnames = @("employees", "customers")  $databases = Get-VEMDBDatabase -Session $session[1] -Name $dbnames |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the second restore session in the array.   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary MongoDB databases. 2. Run the Get-VEMDBDatabase cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. Set the $dbnames variable as the Name parameter value. Save the result to the $databases variable to be able to use it with other cmdlets. |

Related Commands

[Get-VEMDBRestoreSession](get-vemdbrestoresession.md)



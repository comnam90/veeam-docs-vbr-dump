---
title: "Get-VEMDBCollection"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbcollection.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backed-up MongoDB collections.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all collections in a particular database.

|  |
| --- |
| Get-VEMDBCollection [-Database] <VEMDBDatabase> [-Name <String[]>] [<CommonParameters>] |

* Get all collections in the restore point.

|  |
| --- |
| Get-VEMDBCollection [-Session] <VEMDBRestoreSession> [-Name <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up MongoDB collections. After you get the backed-up collections, you can use the [New-VEMDBCollectionRestoreOptions](new-vemdbcollectionrestoreoptions.md) cmdlet to specify the required restore options.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with MongoDB data. | Accepts the [VEMDBRestoreSession](vemdbrestoresession.md) object. To get this object, run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Database | Specifies the MongoDB database on which the collections reside. | Accepts the [VEMDBDatabase](vemdbdatabase.md) object. To get this object, run the [Get-VEMDBDatabase](get-vemdbdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names of MongoDB collections. The cmdlet will return an array of collections located on the restore point or the specified database.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBCollection](vemdbcollection.md)[] array that contains backed-up MongoDB collections.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All MongoDB Collections Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get an array of all MongoDB collections within the specified restore session.  |  | | --- | | $session = Get-VEMDBRestoreSession  $collections = Get-VEMDBCollection -Session $session[1] |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the second restore session in the array).   1. Run the Get-VEMDBCollection cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $collections variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting MongoDB Collections with Specified Names

|  |  |
| --- | --- |
| This example shows how to get an array of MongoDB collections with the specified names.  |  | | --- | | $session = Get-VEMDBRestoreSession  $collectionnames = @("location1", "location2")  $collections = Get-VEMDBCollection -Session $session[1] -Name $collectionnames |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the second restore session in the array.   1. Declare the $collectionnames variable. Assign to this variable an array with the names of the necessary MongoDB collections. 2. Run the Get-VEMDBCollection cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. Set the $collectionnames variable as the Name parameter value. Save the result to the $collections variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting MongoDB Collections from Database

|  |  |
| --- | --- |
| This example shows how to get an array of MongoDB collections from a specific database.  |  | | --- | | $session = Get-VEMDBRestoreSession  $databases = Get-VEMDBDatabase -Session $session[0]  $collections = Get-VEMDBCollection -Database $databases[0] |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).   1. Run the [Get-VEMDBDatabase](get-vemdbdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $databases variable to be able to use it with other cmdlets. 2. Run the Get-VEMDBCollection cmdlet. Set the $databases variable as the Database parameter value and select the necessary database. Save the result to the $collections variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VEMDBRestoreSession](get-vemdbrestoresession.md)
* [Get-VEMDBDatabase](get-vemdbdatabase.md)

Page updated 7/11/2025

Page content applies to build 13.0.1.1071

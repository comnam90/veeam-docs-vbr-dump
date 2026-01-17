---
title: "New-VEMDBCollectionRestoreOptions"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new-vemdbcollectionrestoreoptions.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# New-VEMDBCollectionRestoreOptions


Short Description

Defines the restore options that you can apply to a restore job.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Specify restore options for a collection stored in the backup repository.

|  |
| --- |
| New-VEMDBCollectionRestoreOptions [-Collection] <VEMDBCollection> [-NewCollectionName <String>] [-NewDatabaseName <String>][<CommonParameters>] |

* Specify restore options for a collection that published collection.

|  |
| --- |
| New-VEMDBCollectionRestoreOptions [-NewCollectionName <String>] [-NewDatabaseName <String>] [-PublishedCollection] <VEMDBPublishedCollection> [<CommonParameters>] |

Detailed Description

This cmdlet creates restore options that you can use in a restore job of MongoDB collections. You can use it to specify the collection you want to restore, the new name for the restored collection, and the name of the database to which the collection will be restored.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Collection | Specifies a backed-up MongoDB collection to which the settings will apply. | Accepts the [VEMDBCollection](vemdbcollection.md) object. To get this object, run the [Get-VEMDBCollection](get-vemdbcollection.md) cmdlet. | True | 1 | True (ByValue) |
| PublishedCollection | Specifies a published MongoDB collection to which the settings will apply. | Accepts the [VEMDBPublishedCollection](vemdbpublishedcollection.md) object. To get this object, run the [Get-VEMDBPublishedCollection](get-vemdbpublishedcollection.md) cmdlet. | True | 1 | True (ByValue) |
| NewDatabaseName | Specifies the name of the database to which the collection will be restored. | String | False | Named | False |
| NewCollectionName | Specifies the new name of the restored collection. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBCollectionRestoreOptions](vemdbcollectionrestoreoptions.md) object that contains the restore options for the specified collection.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Specifying Default Restore Options

|  |  |
| --- | --- |
| This example specifies restore options for the home office collection. The collection will be restored with its original name, to the original database.  |  | | --- | | $session = Get-VEMDBRestoreSession  $collection = Get-VEMDBCollection $session[0] -Name "home office"  $restoreoptions = New-VEMDBCollectionRestoreOptions -Collection $collection |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEMDBCollection](get-vemdbcollection.md) cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. Specify the Name parameter value. Save the result to the $collection variable. 2. Run the New-VEMDBCollectionRestoreOptions cmdlet and set the $collection variable as the Collection parameter value. Save the result to the $restoreoptions variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Specifying New Name for Restored Collection

|  |  |
| --- | --- |
| This example specifies restore settings for the first collection in the employees database. The collection will be restored with a new name, to the original database.  |  | | --- | | $session = Get-VEMDBRestoreSession  $database = Get-VEMDBDatabase -Session $session[0] -Name "employees"  $collection = Get-VEMDBCollection -Database $database[0]  $restoreoptions = New-VEMDBCollectionRestoreOptions -Collection $collection -NewCollectionName "home office" |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEMDBDatabase](get-vemdbdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-VEMDBCollection](get-vemdbcollection.md) cmdlet. Set the $database variable as the Database parameter value and select the necessary database. 3. Run the New-VEMDBCollectionRestoreOptions cmdlet and set the $collection variable as the Collection parameter value. Specify the NewCollectionName parameter value. Save the result to the $restoreoptions variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Specifying New Name for Target Database

|  |  |
| --- | --- |
| This example specifies restore settings for the first collection in the customers database. The collection will be restored with the original name, to a new database.  |  | | --- | | $session = Get-VEMDBRestoreSession  $database = Get-VEMDBDatabase -Session $session[0] -Name "customers"  $collection = Get-VEMDBCollection -Database $database[0]  $restoreoptions = New-VEMDBCollectionRestoreOptions -Collection $collection -NewDatabaseName "sydney" |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore job. In our example, it is the first restore job in the array.   1. Run the [Get-VEMDBDatabase](get-vemdbdatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable. 2. Run the [Get-VEMDBCollection](get-vemdbcollection.md) cmdlet. Set the $database variable as the Database parameter value and select the necessary database. Save the result to the $collection variable. 3. Run the New-VEMDBCollectionRestoreOptions cmdlet and set the $collection variable as the Collection parameter value. Specify the NewDatabaseName parameter value. Save the result to the $restoreoptions variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Specifying Restore Options for Published Collection

|  |  |
| --- | --- |
| This example specifies restore settings for the first collection on the published MongoDB instance. The published collection will be restored with a new name, to a new database.  |  | | --- | | $publishedcollections = Get-VEMDBPublishedCollection -Instance "mongodb01:27018"  $restoreoptions = New-VEMDBCollectionRestoreOptions -PublishedCollection $publishedcollections[0] -NewCollectionName "customers" -NewDatabaseName "detroit" |  Perform the following steps:   1. Run the [Get-VEMDBPublishedCollection](get-vemdbpublishedcollection.md) cmdlet. Specify the Instance parameter value. Save the result to the $publishedcollections variable.   The cmdlet will return an array of collections on the published instance. Note the ordinal number of the necessary published collection. In our example, it is the first collection in the array.   1. Run the New-VEMDBCollectionRestoreOptions cmdlet. Set the $publishedcollections variable as the PublishedCollection parameter value and select the necessary collection. Specify the NewCollectionName parameter value. Specify the NewDatabaseName parameter value. Save the result to the $restoreoptions variable to use it with other cmdlets. |

Related Commands

* [Get-VEMDBRestoreSession](get-vemdbrestoresession.md)
* [Get-VEMDBDatabase](get-vemdbdatabase.md)
* [Get-VEMDBCollection](get-vemdbcollection.md)
* [Get-VEMDBPublishedCollection](get-vemdbpublishedcollection.md)



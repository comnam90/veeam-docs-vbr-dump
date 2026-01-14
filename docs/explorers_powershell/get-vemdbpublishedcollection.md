---
title: "get-vemdbpublishedcollection"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbpublishedcollection.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns published MongoDB collections.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get published collections from the published database.

|  |
| --- |
| Get-VEMDBPublishedCollection [[-Database] <VEMDBPublishedDatabase>] [-Name <String[]>] [<CommonParameters>] |

* Get published collections using the names of the published instances.

|  |
| --- |
| Get-VEMDBPublishedCollection -Instance <String[]> [-Name <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of published MongoDB collections. Once you get the necessary MongoDB collections, you can use the [New-VEMDBCollectionRestoreOptions](new-vemdbcollectionrestoreoptions.md) cmdlet to specify the required restore options.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a published MongoDB database. The cmdlet will return an array of collections that belong to the database. | Accepts the [VEMDBPublishedDatabase](vemdbpublisheddatabase.md) object. To get this object, run the [Get-VEMDBPublishedDatabase](get-vemdbpublisheddatabase.md) cmdlet. | False | 0 | True (ByValue) |
| Instance | Specifies an array of names of published MongoDB instances, in the <server>:<port> format (for example, mongodb01:27017). The cmdlet will return an array of collections that belong to published instances with those names.  This parameter accepts wildcard characters. | String[] | True | Named | False |
| Name | Specifies an array of names of published MongoDB collections. The cmdlet will return an array of published collections with the specified names.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBPublishedCollection](vemdbpublishedcollection.md)[] array that contains settings of published MongoDB collections.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Published MongoDB Collections

|  |  |
| --- | --- |
| This example shows how to get an array of all published MongoDB collections.  |  | | --- | | Get-VEMDBPublishedCollection | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All MongoDB Collections from Published Database

|  |  |
| --- | --- |
| This example shows how to get an array of published MongoDB collections from a published database.  |  | | --- | | $publisheddatabase = Get-VEMDBPublishedDatabase  $publishedcollections = Get-VEMDBPublishedCollection -Database $publisheddatabase[0] |  Perform the following steps:   1. Run the [Get-VEMDBPublishedDatabase](get-vemdbpublisheddatabase.md) cmdlet. Save the result to the $publisheddatabase variable.   The cmdlet will return an array of published databases. Note the ordinal number of the necessary published database. In our example, it is the first database in the array.   1. Run the Get-VEMDBPublishedCollection cmdlet. Set the $publisheddatabase as the Database parameter value and select the necessary database. Save the result to the $publishedcollections variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All MongoDB Collections from Published Instances

|  |  |
| --- | --- |
| This example shows how to get an array of all MongoDB collections on the specified published MongoDB instances.  |  | | --- | | $instancenames = @("mongodb01:27017", "mongodb02:27017")  $publishedcollections = Get-VEMDBPublishedCollection -Instance $instancenames |  Perform the following steps:   1. Declare the $instancenames variable. Assign to this variable an array with the names of the necessary MongoDB instances. 2. Run the Get-VEMDBPublishedCollection cmdlet. Set the $instancenames variable as the Instance parameter value. Save the result to the $publishedcollections variable to be able to use it with other cmdlets. |

Related Commands

[Get-VEMDBPublishedDatabase](get-vemdbpublisheddatabase.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071

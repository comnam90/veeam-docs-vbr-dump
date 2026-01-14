---
title: "get-vemdbpublisheddatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbpublisheddatabase.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns published MongoDB databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEMDBPublishedDatabase [-Instance <String[]>] [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of published MongoDB databases. Once you get the necessary MongoDB databases, you can use the [Get-VEMDBPublishedCollection](get-vemdbpublishedcollection.md) cmdlet to get an array of published MongoDB collections.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies an array of names of published MongoDB instances, in the <server>:<port> format (for example, mongodb01:27017). The cmdlet will return an array of databases on the specified instances.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| Name | Specifies an array of names of published MongoDB databases. The cmdlet will return an array of databases with the specified names.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBPublishedDatabase](vemdbpublisheddatabase.md)[] array that contains settings of published MongoDB databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Published MongoDB Databases

|  |  |
| --- | --- |
| This example shows how to get an array of all published MongoDB databases.  |  | | --- | | Get-VEMDBPublishedDatabase | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Published MongoDB Databases

|  |  |
| --- | --- |
| This example shows how to get an array of published MongoDB databases with specific names.  |  | | --- | | $databasenames = @("customers", "employees")  $publisheddatabases = Get-VEMDBPublishedDatabase -Name $databasenames |  Perform the following steps:   1. Declare the $databasenames variable. Assign to this variable an array with the names of the necessary MongoDB databases. 2. Run the Get-VEMDBPublishedDatabase cmdlet. Set the $databasenames variable as the Name parameter value. Save the result to the $publisheddatabases variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting MongoDB Databases from Specific Published Instances

|  |  |
| --- | --- |
| This example shows how to get an array of all MongoDB databases on the specified published MongoDB instances.  |  | | --- | | $instancenames = @("mongodb01:27017", "mongodb02:27017")  $publisheddatabases = Get-VEMDBPublishedDatabase -Instance $instancenames |  Perform the following steps:   1. Declare the $instancenames variable. Assign to this variable an array with the names of the necessary MongoDB instances. 2. Run the Get-VEMDBPublishedDatabase cmdlet. Set the $instancenames variable as the Instance parameter value. Save the result to the $publisheddatabases variable to be able to use it with other cmdlets. |

Page updated 7/29/2025

Page content applies to build 13.0.1.1071

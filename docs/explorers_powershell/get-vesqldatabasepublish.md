---
title: "Get-VESQLDatabasePublish"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqldatabasepublish.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLDatabasePublish


Short Description

Returns active publishing jobs for backed-up Microsoft SQL Server databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a publishing job using the job ID.

|  |
| --- |
| Get-VESQLDatabasePublish -JobId <Guid> [<CommonParameters>] |

* Get a publishing job using database parameters.

|  |
| --- |
| Get-VESQLDatabasePublish [-DatabaseName <String[]>] [-ServerName <String[]>] [-InstanceName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about the publishing process for backed-up Microsoft SQL Server databases.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| JobId | Specifies the job ID of the required publishing job. The cmdlet will return information about the publishing process performed for the specified database. | Guid | True | Named | True (ByValue) |
| DatabaseName | Specifies an array of names of Microsoft SQL Server databases. The cmdlet will return an array of databases with the specified names that have ongoing publishing jobs.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| InstanceName | Specifies an array of names of Microsoft SQL Server instances. The cmdlet will return an array of databases on the specified instances that have ongoing publishing jobs.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| ServerName | Specifies an array of names of target Microsoft SQL Server machines (as DNS names or IP addresses). The cmdlet will return an array of databases that have ongoing publishing jobs to the specified target servers.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLDatabasePublish](vesqldatabasepublish.md)[] array that contains information about the publishing process of Microsoft SQL Server databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Publishing Jobs

|  |  |
| --- | --- |
| This command returns all active Microsoft SQL Server publishing jobs. Save the result to the $publish variable to be able to use it with other cmdlets.  |  | | --- | | $publish = Get-VESQLDatabasePublish | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Publishing Job by Job ID

|  |  |
| --- | --- |
| This example shows how to get a specific publishing job by its job ID.  |  | | --- | | Get-VESQLDatabasePublish  $publish = Get-VESQLDatabasePublish -JobId "9c1b10de-7236-4905-a817-70db4e003f39" |  Perform the following steps:   1. Run the Get-VESQLDatabasePublish cmdlet. This command returns all active Microsoft SQL Server publishing jobs. Save the JobId value for the publishing job that you need. 2. Run the Get-VESQLDatabasePublish cmdlet. Specify the JobId parameter value. Save the result to the $publish variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Publishing Jobs for Databases with Specific Names on Specific Instances

|  |  |
| --- | --- |
| This example shows how to get an array of active publishing jobs for databases with specific names located on specific instances.  |  | | --- | | $dbnames = @("fiscal", "sales", "IT")  $instancenames = @("instance1", "instance2")  $publish = Get-VESQLDatabasePublish -DatabaseName $dbnames -InstanceName $instancenames |  Perform the following steps:   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the Microsoft SQL Server instances that you want to query. 3. Run the Get-VESQLDatabasePublish cmdlet. Set the $dbnames variable as the DatabaseName parameter value. Set the $instancenames variable as the InstanceName parameter value. Save the result to the $publish variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting All Publishing Jobs to Specific Target Servers

|  |  |
| --- | --- |
| This example shows how to get an array of active publishing jobs to specific target servers.  |  | | --- | | $targetservernames = @("srv89", "srv90")  $publish = Get-VESQLDatabasePublish -ServerName $targetservernames |  Perform the following steps:   1. Declare the $targetservernames variable. Assign to this variable an array with the names of the necessary target servers. 2. Run the Get-VESQLDatabasePublish cmdlet. Set the $targetservernames variable as the ServerName parameter value. Save the result to the $publish variable to be able to use it with other cmdlets. |

Page updated 2026-03-16


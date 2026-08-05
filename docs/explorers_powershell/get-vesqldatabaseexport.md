---
title: "Get-VESQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqldatabaseexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLDatabaseExport


Short Description

Returns Microsoft SQL Server databases with ongoing export jobs.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an export job using the job ID.

|  |
| --- |
| Get-VESQLDatabaseExport -JobId <Guid> [<CommonParameters>] |

* Get an export job using database parameters.

|  |
| --- |
| Get-VESQLDatabaseExport [-DatabaseName <String[]>] [-InstanceName <String[]>] [-ServerName <String[]>] [-TargetHost <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Microsoft SQL Server databases with ongoing export jobs.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| JobId | Specifies the job ID of the required export job. The cmdlet will return information about the export process performed for the specified database. | GUID | True | Named | True (ByValue) |
| DatabaseName | Specifies an array of names of Microsoft SQL Server databases. The cmdlet will return an array of databases with the specified names that have ongoing export jobs.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| InstanceName | Specifies an array of names of Microsoft SQL Server instances. The cmdlet will return an array of databases on the specified instances that have ongoing export jobs.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| ServerName | Specifies an array of names of Microsoft SQL Server machines (as DNS names or IP addresses). The cmdlet will return an array of databases on the specified servers that have ongoing export jobs.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| TargetHost | Specifies an array of names of target Microsoft SQL Server servers (as DNS names or IP addresses) for export operations. The cmdlet will return an array of databases that are being exported to the specified target servers.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLDatabaseExport](vesqldatabaseexport.md)[] array that contains ongoing export jobs for Microsoft SQL Server databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Export Jobs

|  |  |
| --- | --- |
| This command returns all active Microsoft SQL Server export jobs. Save the result to the $export variable to be able to use it with other cmdlets.  |  | | --- | | $export = Get-VESQLDatabaseExport | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Export Job by Job ID

|  |  |
| --- | --- |
| This example shows how to get a specific export job by its job ID.  |  | | --- | | Get-VESQLDatabaseExport  $export = Get-VESQLDatabaseExport -JobId "9c1b10de-7236-4905-a817-70db4e003f39" |  Perform the following steps:   1. Run the Get-VESQLDatabaseExport cmdlet. This command returns all active Microsoft SQL Server export jobs. Save the JobId value for the export job that you need. 2. Run the Get-VESQLDatabaseExport cmdlet. Specify the JobId parameter value. Save the result to the $export variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Export Jobs for Databases with Specific Names on Specific Instances

|  |  |
| --- | --- |
| This example shows how to get an array of active export jobs for databases with specific names located on specific instances.  |  | | --- | | $dbnames = @("fiscal", "sales", "IT")  $instancenames = @("instance1", "instance2")  $export = Get-VESQLDatabaseExport -DatabaseName $dbnames -InstanceName $instancenames |  Perform the following steps:   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary Microsoft SQL Server databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the Microsoft SQL Server instances that you want to query. 3. Run the Get-VESQLDatabaseExport cmdlet. Set the $dbnames variable as the DatabaseName parameter value. Set the $instancenames variable as the InstanceName parameter value. Save the result to the $export variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting All Export Jobs to Specific Target Servers

|  |  |
| --- | --- |
| This example shows how to get an array of active export jobs to specific target servers.  |  | | --- | | $targetservernames = @("srv89", "srv90")  $export = Get-VESQLDatabaseExport -TargetHost $targetservernames |  Perform the following steps:   1. Declare the $targetservernames variable. Assign to this variable an array with the names of the necessary target servers. 2. Run the Get-VESQLDatabaseExport cmdlet. Set the $targetservernames variable as the TargetHost parameter value. Save the result to the $export variable to be able to use it with other cmdlets. |

Page updated 2026-02-05


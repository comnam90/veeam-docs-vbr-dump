---
title: "Get-VEPSQLPublishedDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqlpublisheddatabase.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---

# Get-VEPSQLPublishedDatabase


Short Description

Returns published PostgreSQL databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLPublishedDatabase [[-Name] <String[]>] [[-InstanceName] <String[]>] [[-ServerName] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of published PostgreSQL databases. Once you get the necessary PostgreSQL database, you can use [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md) cmdlet to export it.

Note that you will only get an array of PostgreSQL databases published with PowerShell. The cmdlet does not return PostgreSQL databases published in the Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of PostgreSQL databases. The cmdlet will return an array of databases with the specified names. | String[] | False | 0 | False |
| InstanceName | Specifies an array of names of PostgreSQL instances. The cmdlet will return an array of databases on the specified instances. | String[] | False | 1 | False |
| ServerName | Specifies an array of names of target PostgreSQL servers (as DNS names or IP addresses). The cmdlet will return an array of databases published on the specified servers. | String[] | False | 2 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLPublishedDatabase](vepsqlpublisheddatabase.md)[] array that contains settings of published PostgreSQL databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Published PostgreSQL Databases

|  |  |
| --- | --- |
| This example shows how to get an array of all published PostgreSQL databases.  |  | | --- | | Get-VEPSQLPublishedDatabase | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Published PostgreSQL Databases with Specific Names Belonging to Specific Instances

|  |  |
| --- | --- |
| This example shows how to get an array of published PostgreSQL databases with specific names belonging to specific instances on the backup file.  |  | | --- | | $dbnames = @("fiscal", "sales")  $instancenames = @("rhel01:5433", "rhel01:5434")  $database = Get-VEPSQLPublishedDatabase -Name $dbnames -InstanceName $instancenames |  Perform the following steps:   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary PostgreSQL databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the PostgreSQL instances that you want to query. 3. Run the Get-VEPSQLPublishedDatabase cmdlet. Set the $dbnames variable as the Name parameter value and set the $instancenames variable as the InstanceName parameter value. Save the result to the $database variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All PostgreSQL Databases Published on Specific Servers

|  |  |
| --- | --- |
| This example shows how to get an array of all PostgreSQL databases published on the specified servers.  |  | | --- | | $servernames = @("rhel01", "rhel02")  $database = Get-VEPSQLPublishedDatabase -ServerName $servernames |  Perform the following steps:   1. Declare the $servernames variable. Assign to this variable an array with the names of the necessary servers with PostgreSQL. 2. Run the Get-VEPSQLPublishedDatabase cmdlet. Set the $servernames variable as the ServerName parameter value. Save the result to the $database variable to be able to use it with other cmdlets. |



---
title: "Get-VEPSQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqldatabaseexport.html"
last_updated: "7/9/2025"
product_version: "13.0.1.1071"
---

# Get-VEPSQLDatabaseExport


Short Description

Returns PostgreSQL databases with ongoing export sessions.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLDatabaseExport [-Name <String[]>] [-InstanceName <String[]>] [-ServerName <String[]>] [-TargetServerName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of PostgreSQL databases with ongoing export sessions.

After you get the databases with ongoing export sessions, you can perform the following operations:

* [Restart-VEPSQLDatabaseExport](restart-vepsqldatabaseexport.md)
* [Stop-VEPSQLDatabaseExport](stop-vepsqldatabaseexport.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstanceName | Specifies an array of names of PostgreSQL instances. The cmdlet will return an array of databases on the specified instances that have ongoing export sessions.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| Name | Specifies an array of names of PostgreSQL databases. The cmdlet will return an array of databases with the specified names that have ongoing export sessions.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| ServerName | Specifies an array of names of PostgreSQL servers (as DNS names or IP addresses). The cmdlet will return an array of databases on the specified servers that have ongoing export sessions.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| TargetServerName | Specifies an array of names of target PostgreSQL servers (as DNS names or IP addresses) for export operations. The cmdlet will return an array of databases that are being exported to the specified target servers.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLDatabaseExport](vepsqldatabaseexport.md)[] array that contains ongoing PostgreSQL export sessions.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Export Sessions

|  |  |
| --- | --- |
| This command returns all active PostgreSQL export sessions. Save the result to the $export variable to be able to use it with other cmdlets.  |  | | --- | | $export = Get-VEPSQLDatabaseExport | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All PostgreSQL Export Sessions for Databases with Specific Names on Specific Instances

|  |  |
| --- | --- |
| This example shows how to get an array of active PostgreSQL export sessions for databases with specific names located on specific instances.  |  | | --- | | $dbnames = @("fiscal", "sales", "IT")  $instancenames = @("rhel01:5433", "rhel01:5434")  $export = Get-VEPSQLDatabaseExport -Name $dbnames -InstanceName $instancenames |  Perform the following steps:   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary PostgreSQL databases. 2. Declare the $instancenames variable. Assign to this variable an array with the names of the PostgreSQL instances that you want to query. 3. Run the Get-VEPSQLDatabaseExport cmdlet. Set the $dbnames variable as the Name parameter value. Set the $instancenames variable as the InstanceName parameter value. Save the result to the $export variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All PostgreSQL Export Sessions to Specific Servers

|  |  |
| --- | --- |
| This example shows how to get an array of active PostgreSQL export sessions from backups of specific servers to specific target servers.  |  | | --- | | $targetservernames = @("rhel02", "rhel03")  $export = Get-VEPSQLDatabaseExport -TargetServerName $targetservernames |  Perform the following steps:   1. Declare the $targetservernames variable. Assign to this variable an array with the names of the necessary target servers with PostgreSQL. 2. Run the Get-VEPSQLDatabaseExport cmdlet. Set the $targetservernames variable as the TargetServerName parameter value. Save the result to the $export variable to be able to use it with other cmdlets. |

Related Commands

* [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md)
* [Stop-VEPSQLDatabaseExport](stop-vepsqldatabaseexport.md)



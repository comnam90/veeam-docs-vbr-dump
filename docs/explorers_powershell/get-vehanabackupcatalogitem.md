---
title: "get-vehanabackupcatalogitem"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanabackupcatalogitem.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backup catalog items for a specific SAP HANA database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an array of backups of a specific database made in a certain time span.

|  |
| --- |
| Get-VEHANABackupCatalogItem [-Database] <VEHANADatabase> [[-FromUTC] <DateTime>] [[-ToUTC] <DateTime>] [-Limit <Int64>] [<CommonParameters>] |

* Get the latest backup of a specific database.

|  |
| --- |
| Get-VEHANABackupCatalogItem [-Database] <VEHANADatabase> [-Last] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backups of a specific SAP HANA database that are created by Veeam Plug-in for SAP HANA.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies the database whose backup catalog items you want the cmdlet to return. | Accepts the [VEHANADatabase](vehanadatabase.md) object. To get this object, run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet. | True | 0 | True (ByValue) |
| FromUTC | Specifies the point in time that defines the start of the period for which you want to see backup catalog items.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | 0 | False |
| ToUTC | Specifies the point in time that defines the end of the period for which you want to see backup catalog items.  Note: Make sure that the value you assign to this parameter is converted to Universal Coordinated Time (UTC). | DateTime | False | 0 | False |
| Last | Defines that the cmdlet will only return the latest item in the backup catalog. | SwitchParameter | False | Named | False |
| Limit | Limits the number of backup catalog items returned by the cmdlet. | Int64 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEHANABackupCatalogItem](vehanabackupcatalogitem.md)[] array that contains backups of the selected database.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backups of Specific SAP HANA Database

|  |  |
| --- | --- |
| This example returns all backups of a specific SAP HANA database.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = (Get-VEHANADatabase -System $system)[0]  $backup = Get-VEHANABackupCatalogItem -Database $database |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value. 2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array. 3. Run the Get-VEHANABackupCatalogItem cmdlet and set the $database variable as the Database parameter value. Save the result to the $backup variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SAP HANA Database Backups Created in Specified Time Frame

|  |  |
| --- | --- |
| This command returns all backups of an SAP HANA database made within the last 30 days.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = (Get-VEHANADatabase -System $system)[0]  $fromutc = ((Get-Date).AddDays(-30)).ToUniversalTime()  $toutc = (Get-Date).ToUniversalTime()  Get-VEHANABackupCatalogItem -Database $database -FromUTC $fromutc -ToUTC $toutc -Limit 5 |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value. 2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array. 3. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet to get the current date. Subtract 30 days from this date and convert it to UTC time. Save the result to the $fromutc variable. 4. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet to get the current date. Convert it to UTC time. Save the result to the $fromutc variable. 5. Run the Get-VEHANABackupCatalogItem cmdlet and set the $database variable as the Database parameter value. Set the $fromutc variable as the FromUTC parameter value and set the $toutc variable as the ToUTC parameter value. Use the Limit parameter to specify the number of backups returned by the cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting the Latest Backup of Specific SAP HANA Database

|  |  |
| --- | --- |
| This command returns the latest available backup in the backup catalog of the specified database.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session  $database = (Get-VEHANADatabase -System $system)[0]  $backup = Get-VEHANABackupCatalogItem -Database $database -Last |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore job. In our example, it is the first restore job in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value. 2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array. 3. Run the Get-VEHANABackupCatalogItem cmdlet, set the $database variable as the Database parameter value, and provide the Last parameter. Save the result to the $backup variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VEHANARestoreSession](get-vehanarestoresession.md)
* [Get-VEHANASystem](get-vehanasystem.md)
* [Get-VEHANADatabase](get-vehanadatabase.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071

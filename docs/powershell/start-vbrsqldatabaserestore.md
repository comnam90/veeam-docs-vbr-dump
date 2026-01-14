---
title: "Start-VBRSQLDatabaseRestore (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrsqldatabaserestore.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Start-VBRSQLDatabaseRestore (obsolete)

In this article

Short Description

Starts Microsoft SQL database restore.

|  |
| --- |
| Note |
| This cmdlet is no longer supported, use the [Start-VESQLRestoreSession](https://helpcenter.veeam.com/docs/backup/explorers_powershell/start-vesqlrestoresession.html?ver=120) cmdlet instead. To learn more about the Start-VESQLRestoreSession cmdlet, see the [Veeam Explorers PowerShell Reference](https://helpcenter.veeam.com/docs/backup/explorers_powershell/getting_started.html?ver=120). |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides two parameter sets.

* For restoring to the original location:

|  |
| --- |
| Start-VBRSQLDatabaseRestore -Database <VBRSQLDatabase> [-GuestCredentials <CInternalCredentials>] [-SqlCredentials <CInternalCredentials>] [-ToPointInTime <datetime>] [-Force] [-Wait]  [<CommonParameters>] |

* For restoring to another location:

|  |
| --- |
| Start-VBRSQLDatabaseRestore -Database <VBRSQLDatabase> [-ServerName <string>] [-InstanceName <string>] [-DatabaseName <string>] [-GuestCredentials <CInternalCredentials>] [-SqlCredentials <CInternalCredentials>] [-ToPointInTime <datetime>] [-Force] [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restore of a selected SQL database.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies the database you want to restore. | Accepts the [VBRSQLDatabase](vbrsqldatabase.md) object. To get this object, run the [Get-VBRSQLDatabase](get-vbrsqldatabase.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| ServerName | Used for restoring to another location.  Specifies the name of the target server. The database will be restored to that server. | String | False | Named | False |
| InstanceName | Used for restore to another location.  Specifies the name of the instance. The database will be restored to that instance. | String | False | Named | False |
| DatabaseName | Used for restore to another location.  Specifies the new name of the database. The database will be restored with that name. | String | False | Named | False |
| GuestCredentials | Specifies the user credentials to authenticate with the target server.  If not specified, Veeam will use the credentials indicated in the backup job settings. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| SqlCredentials | Specifies the credentials to authenticate with the target SQL instance.  If not specified, Veeam will use the credentials indicated in the backup job settings. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| ToPointInTime | Used to restore the database to a specific transaction.  Specifies the time of the transaction. | datetime | False | Named | False |
| Force | If set, the command will overwrite the existing database with the database from backup.  Note: the cmdlet will show no prompt. | SwitchParameter | False | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Restoring Microsoft SQL Database to Original Location

This example shows how to restore a database to a selected point in time to the original location.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -SQL -Name "crm\_db"  $locations = Get-VBRSQLDatabase -ApplicationRestorePoint $restorepoint[2] -Name "Locations"  $guestcreds = Get-VBRCredentials -Name "tech\administrator"  $sqlcreds = Get-VBRCredentials -Name "sql\_administrator"  Get-VBRSQLDatabaseRestoreInterval -Database $locations  Start-VBRSQLDatabaseRestore -Database $locations -GuestCredentials $guestcreds -SqlCredentials $sqlcreds -ToPointInTime "10/28/2015 12:33:39 PM" |

1. Get the database you want to restore:

* Run the [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) cmdlet. Provide the SQL parameter value. Specify the Name parameter value. Save it to the $restorepoint variable.
* Run the [Get-VBRSQLDatabase](get-vbrsqldatabase.md) cmdlet. Set the $restorepoint[2] variable as the ApplicationRestorePoint parameter value. Specify the Name parameter value. Save it to the $locations variable.

1. Get the credentials to connect to the server and to the database instance:

* Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save it to the $guestcreds variable.
* Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save it to the $sqlcreds variable.

1. Run the [Get-VBRSQLDatabaseRestoreInterval](get-vbrsqldatabaserestoreinterval.md) cmdlet. Set the $locations variable as the Database parameter value.
2. Run the Start-VBRSQLDatabaseRestore cmdlet. Specify the following settings:

* Set the $locations variable as the Database parameter value.
* Set the $guestcreds variable as the GuestCredentials parameter value.
* Set the $sqlcreds variable as the SqlCredentials parameter value.
* Specify the ToPointInTime parameter value.

Related Commands

* [Get-VBRSQLDatabase](get-vbrsqldatabase.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071

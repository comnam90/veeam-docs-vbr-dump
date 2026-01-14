---
title: "Start-VBROracleDatabaseRestore (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbroracledatabaserestore.html"
last_updated: "2/27/2024"
product_version: "13.0.1.1071"
---

# Start-VBROracleDatabaseRestore (obsolete)

In this article

Short Description

Starts Oracle database restore.

|  |
| --- |
| Note |
| This cmdlet is no longer supported, use the [Start-VEORRestoreSession](https://helpcenter.veeam.com/docs/backup/explorers_powershell/start-veorrestoresession.html?ver=120) cmdlet instead. To learn more about the Start-VEORRestoreSession cmdlet, see the [Veeam Explorers PowerShell Reference](https://helpcenter.veeam.com/docs/backup/explorers_powershell/getting_started.html?ver=120). |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides 2 parameter sets.

* For restoring to original location:

|  |
| --- |
| Start-VBROracleDatabaseRestore -Database <VBROracleDatabase> [-GuestCredentials <CInternalCredentials>] [-OracleExplicitPassword <string>] [-OracleCredentials <CInternalCredentials>] [-ToPointInTime <datetime>] [-Force] [-Wait]  [<CommonParameters>] |

* For restoring to another location:

|  |
| --- |
| Start-VBROracleDatabaseRestore -Database <VBROracleDatabase> [-ServerName <string>] [-HomePath <string>] [-DatabaseGlobalName <string>] [-DatabaseSid <string>] [-GuestCredentials <CInternalCredentials>] [-OracleExplicitPassword <string>] [-OracleCredentials <CInternalCredentials>] [-ToPointInTime <datetime>] [-Force] [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restore of a selected Oracle database.

|  |
| --- |
| ![Start-VBROracleDatabaseRestore (obsolete)](images/icon_note.webp) Note: |
| The OracleExplicitPassword parameter is no longer required. The OracleCredentials parameter must be used instead. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies the database you want to restore. | Accepts the [VBROracleDatabase](vbroracledatabase.md) object. To get this object, run the [Get-VBROracleDatabase](get-vbroracledatabase.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| DatabaseGlobalName | Used for restoring to another location. Specifies the new global name for the database you restore. | String | False | Named | False |
| DatabaseSid | Used for restoring to another location. Specifies the new SID for the database you restore. | String | False | Named | False |
| HomePath | Used for restoring to another location. Specifies the name of the Oracle Home on target for the database you restore. | String | False | Named | False |
| ServerName | Used for restoring to another location. Specifies the target server. The database will be restored to that server. | String | False | Named | False |
| OracleCredentials | Used for restoring Oracle Database 12c or later on Windows server.  Specifies the Oracle Home User account credentials. The cmdlet will use these credentials for starting Oracle Services on the VM guest OS.  If not set, the cmdlet will start the service using the Windows Built-in Account or Virtual Account credentials. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| GuestCredentials | Specifies the user credentials to authenticate with the guest OS of the target server.  If not set, the cmdlet will first try to use credentials specified in the backup job settings, then credentials of a current account. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| OracleExplicitPassword | This parameter is deprecated. Use OracleCredentials instead. | String | False | Named | False |
| ToPointInTime | Used to restore the database to a specific point in time.  Specifies the point in time to restore to. Redo logs replay will bring the database to the state as of at that moment. | DateTime | False | Named | False |
| Force | If set, the command will overwrite the existing database with the database from the backup.  Note: the cmdlet will show no prompt. | SwitchParameter | False | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Restoring Oracle Database to Original Location

This example shows how to restore the Oracle 12c database to a selected point in time to the original location.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -Oracle -Name "oracle\_prod"  $locations = Get-VBROracleDatabase -ApplicationRestorePoint $restorepoint[2] -Name "Products"  $guestcreds = Get-VBRCredentials -Name "tech\administrator"  $oraclehomecreds = Get-VBRCredentials -Name "oracleuser1"  Get-VBROracleDatabaseRestoreInterval -Database $locations  Start-VBROracleDatabaseRestore -Database $locations -GuestCredentials $guestcreds -OracleCredentials $oraclehomecreds -ToPointInTime "10/28/2015 12:33:39 PM" |

* Get the database you want to restore:

* Run the [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) cmdlet. Provide the Oracle parameter. Specify the Name parameter value. Save the result to the $restorepoint variable.

* Run the [Get-VBROracleDatabase](get-vbroracledatabase.md) cmdlet. Set the $restorepoint[2] variable as the ApplicationRestorePoint parameter value. Specify the Name parameter value. Save the result to the $locations variable.

* Get the credentials to connect to the server guest OS (Windows in this example) and to the Oracle database:

* Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $guestcreds variable.
* Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $oraclehomecreds variable.

* Run the [Get-VBROracleDatabaseRestoreInterval](get-vbroracledatabaserestoreinterval.md) cmdlet. Set the the $locations variable as the Database parameter value.
* Run the Start-VBROracleDatabaseRestore cmdlet. Specify the following settings:
* Set the the $locations variable as the Database parameter value.
* Set the the $guestcreds variable as the GuestCredentials parameter value.
* Set the the $oraclehomecreds variable as the OracleCredentials parameter value.
* Specify the ToPointInTime parameter value.

Related Commands

* [Get-VBROracleDatabase](get-vbroracledatabase.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 2/27/2024

Page content applies to build 13.0.1.1071

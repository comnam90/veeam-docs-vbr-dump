---
title: "start-vehanadatabaserestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vehanadatabaserestore.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restores a backed-up SAP HANA database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore a tenant SAP HANA database to another server using a point-in-time state of the backup file.

|  |
| --- |
| Start-VEHANADatabaseRestore -TargetServerName <String> -TargetSystemName <String> [-TargetDatabaseName <String>] [-Database] <VEHANADatabase> -PointInTime <DateTime> -TimeZone <TimeZoneInfo> [-TargetSystemUserPassword <SecureString>] [-GuestCredential <PSCredential>] [-ApplicationCredential <PSCredential>] [-UseHttps] [-UseSSL] [-ClientCertificatePath <String>] [-ClientCertificatePassword <SecureString>] [-Force] [<CommonParameters>] |

* Restore a tenant SAP HANA database to another server using a specific backup.

|  |
| --- |
| Start-VEHANADatabaseRestore -TargetServerName <String> -TargetSystemName <String> [-TargetDatabaseName <String>] [-Backup] <VEHANABackupCatalogItem> [-TargetSystemUserPassword <SecureString>] [-GuestCredential <PSCredential>] [-ApplicationCredential <PSCredential>] [-UseHttps] [-UseSSL] [-ClientCertificatePath <String>] [-ClientCertificatePassword <SecureString>] [-Force] [<CommonParameters>] |

* Restore a tenant SAP HANA database to another server using a backup prefix.

|  |
| --- |
| Start-VEHANADatabaseRestore -TargetServerName <String> -TargetSystemName <String> [-TargetDatabaseName <String>] [-Database] <VEHANADatabase> -Prefix <String> [-TargetSystemUserPassword <SecureString>] [-GuestCredential <PSCredential>] [-ApplicationCredential <PSCredential>] [-UseHttps] [-UseSSL] [-ClientCertificatePath <String>] [-ClientCertificatePassword <SecureString>] [-Force] [<CommonParameters>] |

* Restore an SAP HANA database to the original server using the latest state of the backup file.

|  |
| --- |
| Start-VEHANADatabaseRestore [-Database] <VEHANADatabase> [-TargetSystemUserPassword <SecureString>] [-GuestCredential <PSCredential>] [-ApplicationCredential <PSCredential>] [-UseHttps] [-UseSSL] [-ClientCertificatePath <String>] [-ClientCertificatePassword <SecureString>] [-Force] [<CommonParameters>] |

* Restore an SAP HANA database to the original server using a point-in-time state of the backup file.

|  |
| --- |
| Start-VEHANADatabaseRestore [-Database] <VEHANADatabase> -PointInTime <DateTime> -TimeZone <TimeZoneInfo> [-TargetSystemUserPassword <SecureString>] [-GuestCredential <PSCredential>] [-ApplicationCredential <PSCredential>] [-ClearLog] [-UseHttps] [-UseSSL] [-ClientCertificatePath <String>] [-ClientCertificatePassword <SecureString>] [-Force] [<CommonParameters>] |

* Restore an SAP HANA database to the original server using a backup prefix.

|  |
| --- |
| Start-VEHANADatabaseRestore [-Database] <VEHANADatabase> -Prefix <String> [-TargetSystemUserPassword <SecureString>] [-GuestCredential <PSCredential>] [-ApplicationCredential <PSCredential>] [-UseHttps] [-UseSSL] [-ClientCertificatePath <String>] [-ClientCertificatePassword <SecureString>] [-Force] [<CommonParameters>] |

* Restore an SAP HANA database to the original server using a specific backup.

|  |
| --- |
| Start-VEHANADatabaseRestore [-Backup] <VEHANABackupCatalogItem> [-TargetSystemUserPassword <SecureString>] [-GuestCredential <PSCredential>] [-ApplicationCredential <PSCredential>] [-UseHttps] [-UseSSL] [-ClientCertificatePath <String>] [-ClientCertificatePassword <SecureString>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet restores a backed-up SAP HANA database. After you start a restore job, you can use the [Get-VEHANARestoreJobActionLogItems](get-vehanarestorejobactionlogitems.md) cmdlet to get an overview of the restore process. You can also stop the restore process with the [Stop-VEHANADatabaseRestore](stop-vehanadatabaserestore.md) cmdlet or restart a failed restore job using the [Restart-VEHANADatabaseRestore](restart-vehanadatabaserestore.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an SAP HANA backup from the backup catalog. | Accepts the [VEHANABackupCatalogItem](vehanabackupcatalogitem.md) object. To get this object, run the [Get-VEHANABackupCatalogItem](get-vehanabackupcatalogitem.md) cmdlet. | True | 0 | True (ByValue) |
| Database | Specifies an SAP HANA database. The cmdlet will start a restore job for the specified database. | Accepts the [VEHANADatabase](vehanadatabase.md) object. To get this object, run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet. | True | 0 | True (ByValue) |
| ApplicationCredential | Specifies the credentials for the target SAP HANA system.  Note: This parameter is obligatory when the plug-in on the target machine is managed by a standalone Veeam Plug-in for SAP HANA. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| ClearLog | Clears the log area and restores the database as of the last log backup before the selected point in time.  Note: To ensure stable operation of the database on the target system, this parameter is automatically used when restoring a tenant SAP HANA database to another server. | SwitchParameter | False | Named | False |
| ClientCertificatePassword | Specifies the password of the private key used for client validation.  A password is only required if the certificate was exported with password protection enabled. | SecureString | False | Named | False |
| ClientCertificatePath | Specifies the path of the private key used for client validation. | String | False | Named | False |
| Force | Defines that the cmdlet will overwrite an existing SAP HANA database with an SAP HANA database from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| GuestCredential | Specifies the credentials for the target SAP HANA server.  Note: This parameter is obligatory when the plug-in on the target machine is managed by a standalone Veeam Plug-in for SAP HANA. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| PointInTime | Specifies a point in time in the backup file. The cmdlet will restore the database to the state of the specified point in time.  Note: You must specify the time zone of the selected point in time using the TimeZone parameter. | DateTime | True | Named | False |
| Prefix | Specifies the backup prefix of the SAP HANA backup you want to use. | String | True | Named | False |
| TargetDatabaseName | Specifies the name of the restored database on the target server. | String | False | Named | False |
| TargetServerName | Specifies DNS name or IP address of the target server. | String | True | Named | False |
| TargetSystemName | Specifies the name of the target system. | String | True | Named | False |
| TargetSystemUserPassword | Specifies the SYSTEM database user password for the newly created database on the target server.  Note: This parameter is only required if the restore process creates a new database on the target server. | SecureString | False | Named | False |
| TimeZone | Specifies the time zone of the point-in-time state to which you want to restore your data. | TimeZoneInfo | True | Named | False |
| UseHTTPS | Defines that Veeam Explorer for SAP HANA will use the HTTPS protocol for establishing a connection to the target SAP HANA server. | SwitchParameter | False | Named | False |
| UseSSL | Defines that Veeam Explorer for SAP HANA will use the SSL protocol for establishing a connection to the target SAP HANA system. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEHANARestore](vehanarestore.md) object, that contains information about the status of the SAP HANA restore job.

Notes

Start-VEHANADatabaseRestore replaces the deprecated cmdlet Restore-VEHANADatabase. The old cmdlet still works (as an alias of the new cmdlet, with identical functionality), but it may be removed in a future version.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Latest State to Original Location

|  |  |
| --- | --- |
| This example shows how to restore an SAP HANA database to the original location. Note that in this example, the plug-in on the SAP HANA machine is managed by a protection group in Veeam Backup & Replication, so the GuestCredential and ApplicationCredential parameters are not used. The cmdlet will use the credentials specified in the backup policy.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = (Get-VEHANADatabase -System $system)[0]  $restore = Start-VEHANADatabaseRestore -Database $database |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value. 2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array. 3. Run the Start-VEHANADatabaseRestore cmdlet. Set the $database variable as the Database parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Point-in-Time State to Original Location

|  |  |
| --- | --- |
| This example shows how to restore a point-in-time state of an SAP HANA database to the original server. Note that in this example, the plug-in on the SAP HANA machine is managed by a protection group in Veeam Backup & Replication, so the GuestCredential and ApplicationCredential parameters are not used. The cmdlet will use the credentials specified in the backup policy.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = (Get-VEHANADatabase -System $system)[0]  $pit = Get-Date -Date "2023-05-25 15:00:00"  $timezone = Get-TimeZone "Central Europe Standard Time"  $restore = Start-VEHANADatabaseRestore -Database $database -PointInTime $pit -TimeZone $timezone -ClearLog |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value. 2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array. 3. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time of the state to which you want to restore your database. Save the result to the $pit variable. 4. Run the [Get-TimeZone](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.5) cmdlet and specify the required time zone. Save the result to the $timezone variable. 5. Run the Start-VEHANADatabaseRestore cmdlet. Specify the following settings:  * Set the $database variable as the Database value. * Set the $pit variable as the PointInTime value. * Set the $timezone variable as the TimeZone value. * Provide the ClearLog parameter to remove all log segments in the log area and restore the database as of the last log backup before the selected point in time. Note that this may cause loss of in-memory data, so perform this action only if the log area is unavailable.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Tenant Database to Another Server Using Backup Prefix

|  |  |
| --- | --- |
| This example shows how to restore a tenant SAP HANA database to another server using a backup prefix. This example uses secure restore.  Note that Veeam Plug-in for SAP HANA must be installed and properly configured on the target server, and the plug-in account must have the necessary permissions. For more information, see the [Considerations and Limitations](https://helpcenter.veeam.com/docs/vbr/userguide/vehana_considerations.html?ver=13) section of the Veeam Explorers User Guide.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = (Get-VEHANADatabase -System $system)[0]  $guestCredential = Get-Credential  $appCredential = Get-Credential  $newUserPassword = Read-Host -Prompt "Enter password" -AsSecureString  $certificatePassword = Read-Host -Prompt "Enter password" -AsSecureString  $restore = Start-VEHANADatabaseRestore -Database $database -TargetServerName "saphana02" -TargetSystemName "HXE" -Prefix "backup\_1" -GuestCredential $guestCredential -ApplicationCredential $appCredential -TargetSystemUserPassword $newUserPassword -UseHttps -UseSSL -ClientCertificatePath "C:/Users/Admin/Desktop/certificate.pfx" ClientCertificatePassword $certificatePassword |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value. 2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the OS (<sid>adm) user and password that will be used for authenticating to the target SAP HANA server. Save the result to the $guestCredential variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the database user account and password that will be used for authenticating to the target SAP HANA system. Save the result to the $appCredential variable. 5. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $newUserPassword variable. 6. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $certificatePassword variable. 7. Run the Start-VEHANADatabaseRestore cmdlet. Specify the following options:  * Set the $database variable as the Database parameter value. * Specify the TargetServerName parameter value. * Specify the TargetSystemName parameter value. * Specify the Prefix parameter value. * Set the $guestCredential variable as the GuestCredential parameter value. * Set the $appCredential variable as the ApplicationCredential parameter value. * Set the $newUserPassword variable as the TargetSystemUserPassword parameter value. * Provide the UseHttps parameter. * Provide the UseSSL parameter. * Specify the ClientCertificatePath parameter value. * Set the $certificatePassword variable as the ClientCertificatePassword parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Tenant Database to Another Server Using Specific Backup

|  |  |
| --- | --- |
| This example shows how to restore a tenant SAP HANA database to another server using a backup prefix. This example uses secure restore.  Note that Veeam Plug-in for SAP HANA must be installed and properly configured on the target server, and the plug-in account must have the necessary permissions. For more information, see the [Considerations and Limitations](https://helpcenter.veeam.com/docs/vbr/userguide/vehana_considerations.html?ver=13) section of the Veeam Explorers User Guide.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = (Get-VEHANADatabase -System $system)[0]  $backup = (Get-VEHANABackupCatalogItem -Database $database)[2]  $guestCredential = Get-Credential  $appCredential = Get-Credential  $newUserPassword = Read-Host -Prompt "Enter password" -AsSecureString  $certificatePassword = Read-Host -Prompt "Enter password" -AsSecureString  $restore = Start-VEHANADatabaseRestore -Backup $backup -TargetServerName "saphana02" -TargetSystemName "HXE" -GuestCredential $guestCredential -ApplicationCredential $appCredential -TargetSystemUserPassword $newUserPassword -UseHttps -UseSSL -ClientCertificatePath "C:/Users/Admin/Desktop/certificate.pfx" ClientCertificatePassword $certificatePassword |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value. 2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array. 3. Run the [Get-VEHANABackupCatalogItem](get-vehanabackupcatalogitem.md) cmdlet and set the $database variable as the Database parameter value. Select the necessary backup returned by this command and save it to the $backup variable. In our example, it is the third backup in the array. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the OS (<sid>adm) user and password that will be used for authenticating to the target SAP HANA server. Save the result to the $guestCredential variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the database user account and password that will be used for authenticating to the target SAP HANA system. Save the result to the $appCredential variable. 6. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $newUserPassword variable. 7. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $certificatePassword variable. 8. Run the Start-VEHANADatabaseRestore cmdlet. Specify the following options:  * Set the $backup variable as the Backup parameter value. * Specify the TargetServerName parameter value. * Specify the TargetSystemName parameter value. * Set the $guestCredential variable as the GuestCredential parameter value. * Set the $appCredential variable as the ApplicationCredential parameter value. * Set the $newUserPassword variable as the TargetSystemUserPassword parameter value. * Provide the UseHttps parameter. * Provide the UseSSL parameter. * Specify the ClientCertificatePath parameter value. * Set the $certificatePassword variable as the ClientCertificatePassword parameter value.   Save the result to the $restore variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VEHANARestoreSession](get-vehanarestoresession.md)
* [Get-VEHANASystem](get-vehanasystem.md)
* [Get-VEHANADatabase](get-vehanadatabase.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [Get-TimeZone](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.5)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [ConvertTo-SecureString](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.5)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071

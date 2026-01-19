---
title: "Start-VEPSQLInstanceInstantRecovery"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vepsqlinstanceinstantrecovery.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Start-VEPSQLInstanceInstantRecovery


Short Description

Performs instant recovery of a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEPSQLInstanceInstantRecovery [-Instance] <VEPSQLInstance> [[-ToPointInTimeUTC] <DateTime>] [-LinuxCredentials <VEPSQLLinuxCredential>] [-ServerName <String>] [-DataDirectory <String>] [-SshPort <Int32>] [-Force] [-TablespacePath <String[]>] [-Tablespace <VEPSQLTableSpace[]>] [-Port <Int32>] -SwitchOverOptions <VEPSQLIRSwitchOverOptions> [<CommonParameters>] |

Detailed Description

This cmdlet performs instant recovery of a backed-up PostgreSQL instance. You can restore instances to the original location or to another location. For details, see the [Instant Recovery](https://helpcenter.veeam.com/docs/vbr/userguide/vep_ir.html?ver=13) section of the Veeam Explorers User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a PostgreSQL instance. The cmdlet will start an instant recovery session for this instance. | Accepts the [VEPSQLInstance](vepsqlinstance.md) type. To get this object, run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. | True | 0 | True (ByValue) |
| ToPointInTimeUTC | Specifies the point in time in the UTC format within a restore interval of the PostgreSQL instance. The cmdlet will restore the instance to the state of the specified point in time.  Note: If you do not use this parameter, the cmdlet will restore the instance to the time of the restore point used to start the restore session. | DateTime | False | 1 | False |
| DataDirectory | Specifies a path to the data directory for the recovered PostgreSQL instance. The cmdlet will restore the specified instance to the specified data directory. | String | False | Named | False |
| Force | Defines that the cmdlet will replace the target PostgreSQL instance with the instance from the backup.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| LinuxCredentials | Specifies Linux credentials. The cmdlet will use these credentials to connect to the target PostgreSQL server. | Accepts the [VEPSQLLinuxCredential](vepsqllinuxcredential.md) type. To get this object, run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. | False | Named | True (ByValue) |
| Port | Specifies a port for the published PostgreSQL instance.  Note: The specified port must be free, otherwise the instance cannot be published to the target server. | Int32 | False | Named | False |
| ServerName | Specifies DNS name or IP address of the target server to which the instance will be published. | String | False | Named | False |
| SshPort | Specifies the SSH port number. The cmdlet will use that port to connect to the Linux machine. | Int32 | False | Named | False |
| SwitchOverOptions | Specifies a switchover option: Auto, Manual or Scheduled. | Accepts the [VEPSQLIRSwitchOverOptions](vepsqlirswitchoveroptions.md) type. To get this object, run the [New-VEPSQLIRSwitchOverOptions](new-vepsqlirswitchoveroptions.md) cmdlet. | True | Named | True (ByValue) |
| Tablespace | Specifies an array of tablespace names for the recovered PostgreSQL instance. The cmdlet will restore tablespaces specified in this array.  Consider the following:   * For every PostgreSQL tablespace, you must assign a specific tablespace path. * This parameter must be used together with the TablespacePath parameter. | Accepts the [VEPSQLTableSpace](vepsqltablespace.md)[] type. To get this object, run the [Get-VEPSQLTablespace](get-vepsqltablespace.md) cmdlet. | False | Named | False |
| TablespacePath | Specifies an array of tablespace paths for the recovered PostgreSQL instance. The cmdlet will restore PostgreSQL tablespaces to locations specified in this array.  Note: This parameter must be used together with the Tablespace parameter. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstanceInstantRecovery](vepsqlinstanceinstantrecovery.md) object that contains information about the PostgreSQL instance published within the instant recovery session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Instant Recovery of PostgreSQL Instance to Original Location with Scheduled Switchover

|  |  |
| --- | --- |
| This example shows how to perform instant recovery of an instance to the original location using the scheduled switchover option. The cmdlet will perform switchover at 13:00:00 on 2023-11-24 in the timezone of the backup server. The cmdlet will recover the instance to its latest state on the backup file.  |  | | --- | | $time = Get-Date -Date "2023-11-24 13:00:00"  $timeutc = $time.ToUniversalTime()  $scheduledswitch = New-VEPSQLIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $timeutc  $session = Get-VEPSQLRestoreSession  $instance = Get-VEPSQLInstance -Session $session[0]  $irinstance = Start-VEPSQLInstanceInstantRecovery -Instance $instance[0] -SwitchOverOptions $scheduledswitch |  Perform the following steps:   1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when the switchover must be performed. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $timeutc variable. 3. Run the [New-VEPSQLIRSwitchOverOptions](new-vepsqlirswitchoveroptions.md) cmdlet. Provide the Scheduled parameter and specify the SwitchingTimeUtc parameter value. Save the result to the $scheduledswitch variable. 4. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary instance. 2. Run the Start-VEPSQLInstanceInstantRecovery cmdlet. Set the $instance variable as the Instance parameter value and select the necessary instance. Set the $ScheduledSwitch variable as the SwitchOverOptions parameter value. Save the result to the $irinstance variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Instant Recovery of PostgreSQL Instance to Another Server and Switching Over Manually

|  |  |
| --- | --- |
| This example shows how to perform instant recovery of an instance to another server using the manual switchover option. With this switchover option, you can perform manual switchover with the [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md) cmdlet. The cmdlet will recover the instance to a point-in-time state on the backup file.  |  | | --- | | $time = Get-Date -Date "2023-9-24 15:00:00"  $timeutc = $time.ToUniversalTime()  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $creds = New-VEPSQLLinuxCredential -Account "root" -Password $securepassword  $manualswitch = New-VEPSQLIRSwitchOverOptions -Manual  $session = Get-VEPSQLRestoreSession  $instance = Get-VEPSQLInstance -Session $session[0] -DataDirectory "/var/lib/pgsql/13/data2"  $tbsp = Get-VEPSQLTablespace -Instance $instance  $tbsppaths = @("/var/lib/pgsql/tablespace","/var/lib/pgsql/tablespace2", "/var/lib/pgsql/tablespace3")  $irinstance = Start-VEPSQLInstanceInstantRecovery -Instance $instance -ToPointInTimeUTC $timeutc -DataDirectory "/var/lib/pgsql/13/data" -LinuxCredentials $creds -SshPort 22 -Port 5555 -SwitchOverOptions $manualswitch -Tablespace $tbsp -TablespacePath $tbsppaths |  Perform the following steps:   1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet. Specify the Date parameter value to set the point in time to which the instance must be recovered. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $timeutc variable.  1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the [New-VEPSQLLinuxCredential](new-vepsqllinuxcredential.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $creds variable. 3. Run the [New-VEPSQLIRSwitchOverOptions](new-vepsqlirswitchoveroptions.md) cmdlet. Provide the Manual parameter. Save the result in the $ManualSwitch variable. 4. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary session. Specify the DataDirectory parameter value. Save the result to the $instance variable. 2. Run the [Get-VEPSQLTablespace](get-vepsqltablespace.md) cmdlet to get the list of tablespace names for the recovered PostgreSQL instance. Set the $instance variable as the Instance parameter value. Save the result to the $tbsp variable. 3. Declare the $tbsppaths variable. Assign to this variable an array of tablespace paths for the recovered PostgreSQL instance.  1. Run the Start-VEPSQLInstanceInstantRecovery cmdlet. Specify the following options:  * Set the $instance variable as the Instance parameter value. * Set the $timeutc variable as the ToPointInTimeUTC parameter value. * Specify the DataDirectory parameter value. * Set the $creds variable as the LinuxCredentials parameter value. * Specify the SshPort parameter value. * Specify the Port parameter value. * Set the $ManualSwitch variable as the SwitchOverOptions parameter value. * Set the $tbsp variable as the Tablespace parameter value. * Set the $tbsppaths parameter as the TablespacePath parameter value.   Save the result to the $irinstance variable to use it with other cmdlets. |

Related Commands

* [New-VEPSQLIRSwitchOverOptions](new-vepsqlirswitchoveroptions.md)
* [Get-VEPSQLInstance](get-vepsqlinstance.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

* [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md)
* [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md)



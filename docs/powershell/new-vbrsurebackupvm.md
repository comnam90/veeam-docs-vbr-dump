---
title: "New-VBRSureBackupVM"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsurebackupvm.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRSureBackupVM


Short Description

Defines VMs to add to the SureBackup job or to the application group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define VMs that the cmdlet will add to the SureBackup job or to the application group using a job.

|  |
| --- |
| New-VBRSureBackupVM -VM <CObjectInJob> [-Role <VBRSureBackupRole[]>] [-TestScript <VBRSureBackupTestScript[]>] [-StartupOptions <VBRSureBackupStartupOptions>] [-Credentials <CCredentials>] [-Exclude]  [<CommonParameters>] |

* Define VMs that the cmdlet will add to the SureBackup job and to the application group using a restore point.

|  |
| --- |
| New-VBRSureBackupVM -RestorePoint <COib> [-Role <VBRSureBackupRole[]>] [-TestScript <VBRSureBackupTestScript[]>] [-StartupOptions <VBRSureBackupStartupOptions>] [-Credentials <CCredentials>] [-Exclude]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSureBackupVM object that defines VMs that you want to add to the SureBackup job or to the application group.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VM | Specifies VMs added to a job. The cmdlet will add these VMs to the SureBackup job or to the application group. | Accepts the CObjectInJob object. To get this object, run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. | True | Named | True (ByValue, |
| RestorePoint | Specifies VMs added to a restore point. The cmdlet will add these VMs to the SureBackup job or to the application group. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Role | Specifies a role of VMs that you want to add to the SureBackup job or to the application group. The cmdlet will assign the specified role to VMs. You can specify either of the following roles:   * DNSServer * GlobalCatalog * MailServer * SQLServer * WebServer * DomainControllerAuthoritative * DomainControllerNonAuthoritative * VBO | VBRSureBackupRole[] | False | Named | False |
| StartupOptions | Specifies startup settings for VMs that you want to add to the application group. Veeam Backup & Replication will apply these startup options to VMs. | Accepts the VBRSureBackupStartupOptions object. To get this object, run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. | False | Named | False |
| Credentials | Specifies credentials to access VMs and run verification scripts. If you do not specify this parameter, the cmdlet will use the account under which Veeam Backup & Replication is currently running. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| TestScript | Specifies a script for VMs that you want to add to the SureBackup job or to the application group. Veeam Backup & Replication will run this script to verify the role of VMs. | Accepts the VBRSureBackupTestScript[] object. To get this object, run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. | False | Named | False |
| Exclude | Defines that the cmdlet will exclude VMs from the SureBackup job.  You can exclude VMs from the SureBackup job only if they were added through the linked backup or replication job. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupVM object that defines VMs added to the SureBackup job or the application group.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining VM and VM Roles to Add to Application Group Using Job

|  |  |
| --- | --- |
| This example shows how to define an application group settings. The cmdlet will add Winsrv2047 VM to the application group using a job and will assign the mail server role to this VM.  |  | | --- | | $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job -Name "Winsrv2047"  New-VBRSureBackupVM -VM $backupobject -Role MailServer |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Specify the Name parameter value. Save the result to the $backupobject variable. 3. Run the New-VBRSureBackupVM cmdlet. Set the $backupobject variable as the VM parameter value. Set the MailServer option for the Role parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining VM and VM Roles to Add to Application Group Using Restore Point

|  |  |
| --- | --- |
| This example shows how to define an application group settings. The cmdlet will add Winsrv2047 VM to the application group using a restore point and will assign the mail server role to this VM.  |  | | --- | | $backup = Get-VBRBackup -Name "MSExchange"  $restPoint = Get-VBRRestorePoint -Name "Winsrv2047" -Backup $backup  New-VBRSureBackupVM -RestorePoint $restPoint -Role MailServer |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Set the $backup variable as the Backup parameter value. Save the result to the $restPoint variable. 3. Run the New-VBRSureBackupVM cmdlet. Set the $restPoint variable as the RestorePoint parameter value. Set the MailServer option for the Role parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Verification Script for VM

|  |  |
| --- | --- |
| This example shows how to define the Winsrv2047 VM to add to the application group. The cmdlet will define the Winsrv2047 VM with the following settings:   * The Winsrv2047 VM will have the DNS Server role. * Veeam Backup & Replication will run a script to verify applications inside the Winsrv2047 VM.     |  | | --- | | $script = New-VBRSureBackupTestScript -PredefinedApplication DNSServer  $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job -Name "Winsrv2047"  New-VBRSureBackupVM -VM $backupobject -Role DNSServer -TestScript $script |  Perform the following steps:   1. Run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. Set the DNSServer option for the PredefinedApplication parameter. Save the result to the $script variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 3. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Specify the Name parameter value. Save the result to the $backupobject variable. 4. Run the New-VBRSureBackupVM cmdlet. Set the $backupobject variable as the VM parameter value. Set the DNSServer option for the Role parameter. Set the $script variable as the TestScript parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Defining Startup settings of VMs

|  |  |
| --- | --- |
| This example shows how to define the Winsrv2047 VM to add to the application group. The cmdlet will define the Winsrv2047 VM with the following settings:   * The Winsrv2047 VM will have the DNS Server role. * Veeam Backup & Replication will run a script to verify applications inside the Winsrv2047 VM. * The period that is required for VMs to boot is set to 200 seconds. * The timeout required to initialize applications on VMs is set to 150 seconds. * The amount of memory provided for VMs is set to 80 percent.     |  | | --- | | $startupoptions = New-VBRSureBackupStartupOptions -MaximumBootTime 200  -ApplicationInitializationTimeout 150 -AllocatedMemory 80 -PingCheck -HeartbeatCheck  $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job Name "Winsrv2047"  New-VBRSureBackupVM -VM $backupobject -Role DNSServer -StartupOptions $startupoptions |  Perform the following steps:   1. Run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $startupoptions variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 3. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Specify the Name parameter value. Save the result to the $backupobject variable. 4. Run the New-VBRSureBackupVM cmdlet. Set the $backupobject variable as the VM parameter value. Set the DNSServer option for the Role parameter. Set the $startupoptions variable as the StartupOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Excluding VMs From SureBackup Job

|  |  |
| --- | --- |
| This example shows how to exclude the Winsrv2047 VM from the SureBackup job.    |  | | --- | | $sbjob = Get-VBRSureBackupJob  $bjob = Get-VBRJob -Name "Backup"  $vm = Get-VBRJobObject -Job $bjob -Name "Winsrv2047"  $sbvm = New-VBRSureBackupVM -VM $vm -Exclude |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Save the result to the $sbjob variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $bjob variable. 3. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $bjob variable as the Job parameter value. Specify the Name parameter value. Save the result to the $vm variable. 4. Run the New-VBRSureBackupVM cmdlet. Set the $vm variable as the VM parameter value. Provide the Exclude parameter. |

Related Commands

* [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md)
* [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md)
* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRJobObject](get-vbrjobobject.md)
* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRSureBackupJob](get-vbrsurebackupjob.md)



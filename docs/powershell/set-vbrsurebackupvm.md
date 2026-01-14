---
title: "Set-VBRSureBackupVM"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackupvm.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupVM

In this article

Short Description

Modifies settings of VMs added to the SureBackup job or to the application group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupVM -VM <VBRSureBackupVM> [-Role <VBRSureBackupRole[]>] [-TestScript <VBRSureBackupTestScript[]>] [-StartupOptions <VBRSureBackupStartupOptions>] [-Credentials <CCredentials>] [-Exclude]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of VMs added to the SureBackup job or to the application group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VM | Specifies a VM whose settings you want to modify. | Accepts the VBRSureBackupVM object. To creates this object, run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. | True | Named | True (ByValue, |
| Role | Specifies roles of VMs that you want to add to the application group. The cmdlet will assign the specified role to VMs. You can specify either of the following roles:   * DNSServer * GlobalCatalog * MailServer * SQLServer * WebServer * DomainControllerAuthoritative * DomainControllerNonAuthoritative * VBO | VBRSureBackupRole[] | False | Named | False |
| TestScript | Specifies a script for VMs that you want to add to the application group. Veeam Backup & Replication will run this script to verify the role of VMs. | Accepts the VBRSureBackupTestScript[] object. To get this object, run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. | False | Named | False |
| StartupOptions | Specifies startup settings for VMs that you want to add to the application group. Veeam Backup & Replication will apply these startup options to VMs. | Accepts the VBRSureBackupStartupOptions object. To get this object, run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. | False | Named | False |
| Credentials | Specifies credentials to access VMs and run verification scripts. If you do not specify this parameter, the cmdlet will use the account under which Veeam Backup & Replication is currently running. | CCredentials | False | Named | False |
| Exclude | Defines that the cmdlet will exclude VMs from the SureBackup job.  You can exclude VMs from the SureBackup job only if they were added through the linked backup or replication job. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupVM object that defines VMs added to the SureBackup job or the application group.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Role of VM

|  |  |
| --- | --- |
| This example shows how to modify a role of the VM that you want to add to the application group. The cmdlet will change the role of the VM from the Mail Server role to the Global Catalog role.  |  | | --- | | $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job -Name "Winsrv2047"  $vm = New-VBRSureBackupVM -VM $backupobject -Role MailServer  Set-VBRSureBackupVM -VM $vm -Role GlobalCatalog |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Specify the Name parameter value. Save the result to the $backupobject variable. 3. Run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. Set the $backupobject variable as the VM parameter value. Set the MailServer option for the Role parameter. 4. Run the Set-VBRSureBackupVM cmdlet. Set the $vm variable as the VM parameter value. Set the GlobalCatalog option for the Role parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Startup Settings of VMs

|  |  |
| --- | --- |
| This example shows how to modify startup settings of the VM that you want to add to the application group. The VM will have the following startup settings:   * The period that is required for VMs to boot is set to 100 seconds. * The timeout required to initialize applications on VMs is set to 150 seconds. * The amount of memory provided for VMs is set to 60 percent.     |  | | --- | | $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job -Name "Winsrv2047"  $vm = New-VBRSureBackupVM -VM $backupobject -Role MailServer  $startupoptions = New-VBRApplicationGroupStartupOptions -MaximumBootTime 100 -ApplicationInitializationTimeout 150 -AllocatedMemory 60  Set-VBRSureBackupVM -VM $vm -StartupOptions $startupoptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Specify the Name parameter value. Save the result to the $backupobject variable. 3. Run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. Set the $backupobject variable as the VM parameter value. Set the MailServer option for the Role parameter. Save the result to the $vm variable. 4. Run the [New-VBRApplicationGroupStartupOptions](new-vbrapplicationgroupstartupoptions_surebackup.md) cmdlet. Specify the MaximumBootTime, ApplicationInitializationTimeout and AllocatedMemory parameter values. Save the result to the $startupoptions variable. 5. Run the Set-VBRSureBackupVM cmdlet. Set the $vm variable as the VM parameter value. Set the $startupoptions variable as the StartupOptions parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRJobObject](get-vbrjobobject.md)
* [New-VBRSureBackupVM](new-vbrsurebackupvm.md)
* [New-VBRApplicationGroupStartupOptions](new-vbrapplicationgroupstartupoptions_surebackup.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071

---
title: "New-VBRSureBackupLinkedJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsurebackuplinkedjob.html"
last_updated: "11/24/2025"
product_version: "13.0.1.1071"
---

# New-VBRSureBackupLinkedJob


Short Description

Defines jobs linked with the SureBackup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSureBackupLinkedJob -Job <CBackupJob> [-Role <VBRSureBackupRole[]> {DNSServer | GlobalCatalog | MailServer | SQLServer | WebServer | DomainControllerAuthoritative | DomainControllerNonAuthoritative | VBO}] [-TestScript <VBRSureBackupTestScript[]>] [-StartupOptions <VBRSureBackupStartupOptions>] [-Credentials <CCredentials>] [-VM <VBRSureBackupVM[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSureBackupLinkedJob object that defines jobs linked with the SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specify a backup or replication job. Veeam Backup & Replication will verify VMs from this job with the SureBackup job. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| Role | Specifies a role that VM from the linked job performs. You can specify either of the following roles:   * DNSServer * GlobalCatalog * MailServer * SQLServer * WebServer * DomainControllerAuthoritative * DomainControllerNonAuthoritative * VBO | VBRSureBackupRole[] | False | Named | False |
| TestScript | Specifies recovery verification scripts for VMs from the linked job. | Accepts the VBRSureBackupTestScript[] object. To create this object, run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. | False | Named | False |
| StartupOptions | Specifies startup settings for VMs from the linked job. | Accepts the VBRSureBackupStartupOptions object. To create this object, run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. | False | Named | False |
| Credentials | Specifies credentials. The cmdlet will use these credentials to authenticate against the VM and to run a recovery verification script. | CCredentials | False | Named | False |
| VM | Specifies an array of VMs. The cmdlet will run a verification script on these VMs. | Accepts the VBRSureBackupV[] object. To create this object, run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupLinkedJob object that defines jobs linked with the SureBackup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Linked Job with Verification Script

|  |  |
| --- | --- |
| This example shows how to define a linked job that will be verified with the SureBackup job. Veeam Backup & Replication will run a verification script to verify the VM with the Global Catalog role has up and running applications for this role.  |  | | --- | | $job = Get-VBRJob -Name "Exchange Job"  $script = New-VBRSureBackupTestScript -PredefinedApplication GlobalCatalog  New-VBRSureBackupLinkedJob -Job $job -Role GlobalCatalog -TestScript $script |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. Specify the GlobalCatalog option as the PredefinedApplication parameter value. Save the result to the $script variable. 3. Run the New-VBRSureBackupLinkedJob cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Specify the GlobalCatalog as the Role parameter value. * Set the $script variable as the TestScript parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Linked Job with Startup Options

|  |  |
| --- | --- |
| This example shows how to define a linked job that will be verified with the SureBackup job. Veeam Backup & Replication will run a verification script to verify the VM with the Global Catalog role has up and running applications for this role.  |  | | --- | | $job = Get-VBRJob -Name "Exchange Job"  $startup = New-VBRSureBackupStartupOptions -MaximumBootTime 200 -ApplicationInitializationTimeout 150 -AllocatedMemory 80 -EnableVMPingCheck -EnableVMHeartbeatCheck  New-VBRSureBackupLinkedJob -Job $job -StartupOptions $startup |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $startup variable. 3. Run the New-VBRSureBackupLinkedJob cmdlet. Set the $job variable as the Job parameter value. Set the $startup variable as the StartupOptions parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md)
* [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md)



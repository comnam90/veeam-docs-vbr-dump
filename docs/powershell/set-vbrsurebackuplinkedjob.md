---
title: "Set-VBRSureBackupLinkedJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackuplinkedjob.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupLinkedJob


Short Description

Modifies settings of jobs linked with the SureBackup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupLinkedJob -LinkedJob <VBRSureBackupLinkedJob> [-Job <CBackupJob>] [-Role <VBRSureBackupRole[]>] [-TestScript <VBRSureBackupTestScript[]>] [-StartupOptions <VBRSureBackupStartupOptions>] [-Credentials <CCredentials>] [-VM <VBRSureBackupVM[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of jobs linked with the SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LinkedJob | Specify a job linked with the SureBackup job. Veeam Backup & Replication will modify settings of this linked job. | Accepts the VBRSureBackupLinkedJob object. To create this object, run the [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md) cmdlet. | True | Named | True (ByValue, |
| Job | Specify a backup or replication job. Veeam Backup & Replication will verify VMs from this job with the SureBackup job. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Role | Specifies a role that VM from the linked job performs. You can specify either of the following roles:   * DNSServer * GlobalCatalog * MailServer * SQLServer * WebServer * DomainControllerAuthoritative * DomainControllerNonAuthoritative * VBO | VBRSureBackupRole[] | False | Named | False |
| TestScript | Specifies recovery verification scripts for VMs from the linked job. | Accepts the VBRSureBackupTestScript[] object. To create this object, run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. | False | Named | False |
| StartupOptions | Specifies startup settings for VMs from the linked job. | Accepts the VBRSureBackupStartupOptions object. To create this object, run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. | False | Named | False |
| Credentials | Specifies credentials. The cmdlet will use these credentials to authenticate against the VM and to run a recovery verification script. | CCredentials | False | Named | False |
| VM | Specifies an array of VMs. The cmdlet will run a verification script on these VMs. | Accepts the VBRSureBackupVM[] object. To create this object, run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupLinkedJob object that defines jobs linked with the SureBackup job.

Examples

Modifying Roles of VMs Added to Linked Job

This example shows how to assign the SQLServer role to VMs that are added to the Exchange Job linked job.

|  |
| --- |
| $job = Get-VBRJob -Name "Exchange Job"  Set-VBRSureBackupLinkedJob -Job $job -Role SQLServer |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Set-VBRSureBackupLinkedJob cmdlet. Set the $job variable as the Job parameter value. Set the SQLServer option for the Role parameter.

Related Commands

[Get-VBRJob](get-vbrjob.md)



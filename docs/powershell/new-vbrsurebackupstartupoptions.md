---
title: "New-VBRSureBackupStartupOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsurebackupstartupoptions.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# New-VBRSureBackupStartupOptions


Short Description

Defines startup settings for VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSureBackupStartupOptions -AllocatedMemory <int> -EnableVMHeartbeatCheck -MaximumBootTime <int> -ApplicationInitializationTimeout <int> -EnableVMPingCheck [-DisableWindowsFirewall]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSureBackupStartupOptions object that defines startup settings for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AllocatedMemory | Specifies the amount of memory that you want to pre-allocate to VMs when these VMs start.  Default: 100 percent. | Int32 | True | Named | False |
| EnableVMHeartbeatCheck | Defines that Veeam Backup & Replication will enable a heartbeat test for verified VMs.  Default: False. | SwitchParamter | True | Named | False |
| MaximumBootTime | Specifies the period that is required for VMs to boot.  Default: 600 seconds. | Int32 | True | Named | False |
| ApplicationInitializationTimeout | Specifies the timeout that is required to initialize applications on VMs.  Default: 120 seconds. | Int32 | True | Named | False |
| EnableVMPingCheck | Defines that Veeam Backup & Replication will enable a ping test for verified VMs.  Default: False. | SwitchParamter | True | Named | False |
| DisableWindowsFirewall | Defines that Veeam Backup & Replication will disable Windows Firewall. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSureBackupStartupOptions object that defines startup settings for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Startup Settings for VMs Added to Application Groups

|  |  |
| --- | --- |
| This command specifies startup settings for VMs added to an application group. Veeam Backup & Replication will perform staged restore with the following VM startup settings:   * The period that is required for VMs to boot is set to 200 seconds. * The timeout required to initialize applications on VMs is set to 150 seconds. * The amount of memory provided for VMs is set to 80 percent. * Veeam Backup & Replication will perform heartbeat and ping tests.   |  | | --- | | New-VBRSureBackupStartupOptions -MaximumBootTime 200 -ApplicationInitializationTimeout 150 -AllocatedMemory 80 -EnableVMPingCheck -EnableVMHeartbeatCheck | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Startup Settings with Disabled Verification Tests for VMs Added to Application Groups

|  |  |
| --- | --- |
| This command specifies the following startup settings for VMs added to an application group. Veeam Backup & Replication will perform staged restore with the following VM startup settings:   * The period that is required for VMs to boot is set to 100 seconds. * The timeout required to initialize applications on VMs is set to 200 seconds. * The amount of memory provided for VMs is set to 90 percent. * Veeam Backup & Replication will perform not heartbeat and ping tests.   |  | | --- | | New-VBRSureBackupStartupOptions -MaximumBootTime 100 -ApplicationInitializationTimeout 200 -AllocatedMemory 90 -EnableVMPingCheck:$False -EnableVMHeartbeatCheck:$False | |



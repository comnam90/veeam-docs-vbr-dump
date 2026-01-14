---
title: "Set-VBRSureBackupStartupOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackupstartupoptions.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupStartupOptions

In this article

Short Description

Modifies startup settings for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupStartupOptions -Options <VBRSureBackupStartupOptions> [-AllocatedMemory <Int32>] [-EnableVMHeartbeatCheck] [-MaximumBootTime <Int32>] [-ApplicationInitializationTimeout <Int32>] [-EnableVMPingCheck] [-DisableWindowsFirewall]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies startup settings for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the startup options that you want to modify. | Accepts the VBRSureBackupStartupOptions object. To creates this object, run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. | True | Named | True (ByValue, |
| AllocatedMemory | Specifies the amount of memory that you want to pre-allocate to VMs when these VMs start.  Default: 100 percent. | Int32 | False | Named | False |
| EnableVMHeartbeatCheck | Defines that Veeam Backup & Replication will perform a heartbeat test for verified VMs. | SwitchParamter | False | Named | False |
| MaximumBootTime | Specifies the period that is required for VMs to boot.  Default: 600 seconds. | Int32 | False | Named | False |
| ApplicationInitializationTimeout | Specifies the timeout that is required to initialize applications on VMs.  Default: 120 seconds. | Int32 | False | Named | False |
| EnableVMPingCheck | Defines that Veeam Backup & Replication will perform a ping test for verified VMs. | SwitchParamter | False | Named | False |
| DisableWindowsFirewall | Defines that Veeam Backup & Replication will disable Windows Firewall. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSureBackupStartupOptions object that defines startup settings for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

Examples

Modifying Startup Settings

This example shows how to modify startup settings for VMs to add to application groups. The cmdlet will change the following settings:

* The timeout required to initialize applications on VMs will be changed from 120 to 150 seconds.
* The amount of memory provided for VMs will be changed from 60 to 80 percent.

|  |
| --- |
| $startup = New-VBRSureBackupStartupOptions -MaximumBootTime 200 -ApplicationInitializationTimeout 120 -AllocatedMemory 60 -EnableVMPingCheck -EnableVMHeartbeatCheck  Set-VBRSureBackupStartupOptions -Options $startup -ApplicationInitializationTimeout 150 -AllocatedMemory 80 |

Perform the following steps:

1. Run the [New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $startup variable.
2. Run the Set-VBRSureBackupStartupOptions cmdlet. Specify the following settings:

* Set the $startup as the Options parameter value.
* Specify the ApplicationInitializationTimeout parameter value.
* Specify the AllocatedMemory parameter value.

Related Commands

[New-VBRSureBackupStartupOptions](new-vbrsurebackupstartupoptions.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071

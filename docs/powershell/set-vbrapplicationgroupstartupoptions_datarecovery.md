---
title: "Set-VBRApplicationGroupStartupOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrapplicationgroupstartupoptions_datarecovery.html"
last_updated: "4/2/2024"
product_version: "13.0.1.1071"
---

# Set-VBRApplicationGroupStartupOptions

In this article

Short Description

Modifies VM startup settings for staged restore.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRApplicationGroupStartupOptions -Options <VBRApplicationGroupStartupOptions> [-MaximumBootTime <int>] [-ApplicationInitializationTimeout <int>] [-MemoryAllocationPercent <int>] [-HeartbeatCheck] [-PingCheck]  [<CommonParameters>] |

Detailed Description

The cmdlet modifies startup settings for staged restore.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the VM startup settings that you want to modify. | Accepts the VBRApplicationGroupStartupOptions object. To get this object, run the [New-VBRApplicationGroupStartupOptions](new-vbrapplicationgroupstartupoptions_surebackup.md) cmdlet. | True | Named | False |
| MaximumBootTime | Specifies the period that is required for VMs to boot.  Default: 600 sec. | Int | False | Named | False |
| ApplicationInitializationTimeout | Specifies a timeout required to initialize applications on VMs.  Default: 120 sec. | Int | False | Named | False |
| MemoryAllocationPercent | Specifies the amount of memory that you want to pre-allocate to VMs when these VMs start.  Default: 100 percent. | Int | False | Named | False |
| HeartbeatCheck | Defines that Veeam Backup & Replication will perform a heartbeat test for verified VMs. | SwitchParameter | False | Named | False |
| PingCheck | Defines that Veeam Backup & Replication will perform a ping test for verified VMs. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRApplicationGroupStartupOptions object that contains VM startup settings for staged restore.

Examples

Modifying Startup Settings for VMs in Application Group

This example shows how to modify startup settings for VMs added to an application group. Veeam Backup & Replication will perform staged restore with the following settings:

* The stabilization period is set to 200 sec.
* The period to initialize the guest applications is set to 150.
* The amount of memory provided for the VM is set to 80 percent.

|  |
| --- |
| $startup = New-VBRApplicationGroupStartupOptions -MaximumBootTime 200 -ApplicationInitializationTimeout 150 -MemoryAllocationPercent 80  $newoptions = Set-VBRApplicationGroupStartupOptions -Options $startup -MaximumBootTime 250 -ApplicationInitializationTimeout 80 -MemoryAllocationPercent 67 |

Perform the following steps:

1. Run the [New-VBRApplicationGroupStartupOptions](new-vbrapplicationgroupstartupoptions_surebackup.md) cmdlet. Specify the MaximumBootTime, ApplicationInitializationTimeout and MemoryAllocationPercent parameter value. Save the result to the $startup variable.
2. Run the Set-VBRApplicationGroupStartupOptions cmdlet. Specify the following settings:

* Set the $startup variable as the Options parameter value.
* Specify the MaximumBootTime parameter value.
* Specify the ApplicationInitializationTimeout parameter value.
* Specify the MemoryAllocationPercent parameter value.

Related Commands

[New-VBRApplicationGroupStartupOptions](new-vbrapplicationgroupstartupoptions_surebackup.md)

Page updated 4/2/2024

Page content applies to build 13.0.1.1071

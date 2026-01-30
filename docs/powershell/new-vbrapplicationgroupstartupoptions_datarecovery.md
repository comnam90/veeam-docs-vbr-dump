---
title: "New-VBRApplicationGroupStartupOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationgroupstartupoptions_datarecovery.html"
last_updated: "4/2/2024"
product_version: "13.0.1.1071"
---

# New-VBRApplicationGroupStartupOptions


Short Description

Creates VM startup settings for staged restore.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationGroupStartupOptions -MaximumBootTime <int> -ApplicationInitializationTimeout <int> -MemoryAllocationPercent <int> [-HeartbeatCheck] [-PingCheck]  [<CommonParameters>] |

Detailed Description

The cmdlet creates the VBRApplicationGroupStartupOptions object that contains VM startup settings for staged restore.

Run the [Start-VBRRestoreVM](start-vbrrestorevm.md) cmdlet to restore VMware VMs with the staged restore option.

Run the [Start-VBRHvRestoreVM](start-vbrhvrestorevm.md) cmdlet to restore Hyper-V VMs with the staged restore option.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| MaximumBootTime | Specifies the period that is required for VMs to boot.  Default: 600 sec. | Int | True | Named | False |
| ApplicationInitializationTimeout | Specifies a timeout required to initialize applications on VMs.  Default: 120 sec. | Int | True | Named | False |
| MemoryAllocationPercent | Specifies the amount of memory that you want to pre-allocate to VMs when these VMs start.  Default: 100 percent. | Int | True | Named | False |
| HeartbeatCheck | Defines that Veeam Backup & Replication will perform a heartbeat test for verified VMs. | SwitchParameter | False | Named | False |
| PingCheck | Defines that Veeam Backup & Replication will perform a ping test for verified VMs. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRApplicationGroupStartupOptions object that contains VM startup settings for staged restore.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Startup Settings

|  |  |
| --- | --- |
| This command defines startup settings for VMs added to an application group. Veeam Backup & Replication will perform staged restore with the following VM startup settings:   * The period that is required for VMs to boot is set to 200 sec. * The timeout required to initialize applications on VMs is set to 150. * The amount of memory provided for VMs is set to 80 percent.   |  | | --- | | $startupoptions = New-VBRApplicationGroupStartupOptions -MaximumBootTime 200 -ApplicationInitializationTimeout 150 -MemoryAllocationPercent 80 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Startup Settings with Heartbeat and Ping Tests

|  |  |
| --- | --- |
| This command defines startup settings for VMs added to an application group. Veeam Backup & Replication will perform staged restore with the following VM startup settings:   * The period that is required for VMs to boot is set to 150 sec. * The timeout required to initialize applications on VMs is set to 130. * The amount of memory provided for VMs is set to 110 percent.   |  | | --- | | $startupoptions = New-VBRApplicationGroupStartupOptions -MaximumBootTime 150 -ApplicationInitializationTimeout 130 -MemoryAllocationPercent 110 -HeartbeatCheck -PingCheck | |



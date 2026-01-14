---
title: "New-VBRFailoverPlanObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfailoverplanobject.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRFailoverPlanObject

In this article

Short Description

Creates the [VBRFailoverPlanObject](vbrfailoverplanobject.md) object.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a VBRFailoverPlanObject object for a specific restore point of a replica.

|  |
| --- |
| New-VBRFailoverPlanObject -RestorePoint <COib> [-BootOrder <int>] [-BootDelay <int>]  [<CommonParameters>] |

* Create a VBRFailoverPlanObject object for a specific VM.

|  |
| --- |
| New-VBRFailoverPlanObject -Vm <IItem> [-BootOrder <int>] [-BootDelay <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRFailoverPlanObject](vbrfailoverplanobject.md) object. This object contains the VM that you want to add to a failover plan. It is used then in the [Add-VBRFailoverPlan](add-vbrfailoverplan.md) cmdlet.

You must create the [VBRFailoverPlanObject](vbrfailoverplanobject.md) object for each VM that you want to add to the failover plan. For each VM, you can set the boot order and the delay time.

* The boot order indicates the order in which the VMs will start by the failover plan. Make sure you set the dependent VMs to start after the VMs they depend on.
* The delay time is an interval between each VM start. Use delay intervals to make sure that some VMs are already running at the moment the dependent VMs start.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the replica that you want to add to the cloud failover plan. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, |
| Vm | Specifies the VM you want to add to the failover plan. | Accepts the IItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| BootOrder | Specifies the order number by which the VM will boot. | Int32 | False | Named | False |
| BootDelay | Specifies the delay time for the VM to boot.  The delay time is set in seconds.  If omitted, the delay time will be set to 60 sec by default.  If you set boot delay to '0' to a number of VMs, these VMs will start simultaneously. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFailoverPlanObject](vbrfailoverplanobject.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Create VBRFailoverPlanObject Object for Group of Servers

|  |  |
| --- | --- |
| This example shows how to create three [VBRFailoverPlanObject](vbrfailoverplanobject.md) objects for the group of mail servers: a DNS server and two Microsoft Exchange servers. The DNS server starts first followed by the two Microsoft Exchange servers started with a delay.  |  | | --- | | $DNS = Find-VBRViEntity -Name "DNSServer" | New-VBRFailoverPlanObject -BootDelay 0  $MSExchange01 = Find-VBRViEntity -Name "MS\_Exchange\_Server\_01" | New-VBRFailoverPlanObject -BootOrder 1  -BootDelay 180  $MSExchange02 = Find-VBRViEntity -Name "MS\_Exchange\_Server\_02" | New-VBRFailoverPlanObject -BootOrder 2  -BootDelay 120 |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the New-VBRFailoverPlanObject cmdlet. Specify the BootDelay parameter value. Save the result to the $DNS variable to be used with other cmdlets. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the New-VBRFailoverPlanObject cmdlet. Specify the BootOrder and BootDelay parameter values. Save the result to the $MSExchange01 variable to be used with other cmdlets. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the New-VBRFailoverPlanObject cmdlet. Specify the BootOrder and BootDelay parameter values. Save the result to the $MSExchange02 variable to be used with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Create VBRFailoverPlanObject Object for Server

|  |  |
| --- | --- |
| This example shows how to create the [VBRFailoverPlanObject](vbrfailoverplanobject.md) objects for the MS\_Exchange\_Server\_01 server.  |  | | --- | | $vm1 = Find-VBRViEntity -Name "MS\_Exchange\_Server\_01"  $MSExchange01 = New-VBRFailoverPlanObject -Vm $vm1 -BootOrder 1 -BootDelay 180 |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm1 variable. 2. Run the New-VBRFailoverPlanObject cmdlet. Specify the following settings:  * Set the $vm1 variable as the Vm parameter value. * Specify the BootOrder parameter value. * Specify the BootDelay parameter value. * Save the result to the $MSExchange01 variable to be used with other cmdlets. |

Related Commands

[Find-VBRViEntity](find-vbrvientity.md)

Page updated 2/12/2024

Page content applies to build 13.0.1.1071

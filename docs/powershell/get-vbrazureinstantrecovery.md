---
title: "Get-VBRAzureInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureinstantrecovery.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAzureInstantRecovery


Short Description

Returns an array of objects on the Instant Recovery to Microsoft Azure operation.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return an array of all objects related to the Instant Recovery to Microsoft Azure operation.

|  |
| --- |
| Get-VBRAzureInstantRecovery [<CommonParameters>] |

* Return specific object related to the Instant Recovery to Microsoft Azure operation.

|  |
| --- |
| Get-VBRAzureInstantRecovery [-InstantRecovery <VBRAzureInstantRecovery>] [<CommonParameters>] |

* Return objects by the IDs of  the Instant Recovery to Microsoft Azure operation.

|  |
| --- |
| Get-VBRAzureInstantRecovery [-Id <guid[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of objects. Each object contains information about the Instant Recovery to Microsoft Azure operation. The objects include the following properties:

* RestorePointId: The ID of the restore point used for recovery.
* Platform: The platform that hosts the recovered workload.
* State: The current state of the Instant Recovery operation.
* TargetVm: The Microsoft Azure VM created during the Instant Recovery process.
* Log: The log sessions for the Instant Recovery to Microsoft Azure operation.
* Id: The ID of the Instant Recovery to Microsoft Azure operation.

You can use this object to get additional log sessions on the Instant Recovery Microsoft Azure operation and to finalize the migration.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the Instant Recovery to Microsoft Azure operations. The cmdlet will return an array of objects with information on these operations. | Accepts the VBRAzureInstantRecovery object. To create this object, run the [Start-VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md) cmdlet. | False | Named | True |
| Id | Specifies an array of IDs of Instant Recovery to Microsoft Azure operations. The cmdlet will return information on these operations. | Guid[] | False | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureInstantRecovery](vbrazureinstantrecovery.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Information on All Instant Recovery to Microsoft Azure Operations

|  |  |
| --- | --- |
| This command returns information on all Instant Recovery to Microsoft Azure operations.  |  | | --- | | Get-VBRAzureInstantRecovery | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Information on Specific Instant Recovery to Microsoft Azure Operation

|  |  |
| --- | --- |
| This command returns information on the Instant Recovery to Microsoft Azure operation that restores the Tech VM.  |  | | --- | | $point = Get-VBRBackup -Name "Tech VM" | Get-VBRRestorePoint -Name "backup-azure-win16-g1" | Sort-Object –Property CreationTime –Descending | Select-Object -First 1  $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Tech.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "swedencentral"  $vmSize = Get-VBRAzureVMSize -Subscription $subscription -Location $location -Name "Standard\_F4s\_v2"  $virtualNetwork = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name tech\* -Location $location  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $virtualNetwork -Name "default"  $group = Get-VBRAzureResourceGroup -Subscription $subscription -Name "tech-ts-group" -Location $location  $session = Start-VBRAzureInstantRecovery -RestorePoint $point -Subscription $subscription -Location $location -VmSize $vmSize -VirtualNetwork $virtualNetwork -VirtualSubnet $subnet -ApplianceSubnet $subnet -VmName "tech-recovered-VM" -ResourceGroup $group -RunAsync  Get-VBRAzureInstantRecovery -InstantRecovery $session |  Perform the following steps:   1. Get the [Instant Recovery to Microsoft Azure](start-vbrazureinstantrecovery.md#example) operation. Save the result to the $session variable. 2. Run the Get-VBRAzureInstantRecovery cmdlet. Set the $session variable as the InstantRecovery parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Information on Instant Recovery to Microsoft Azure Operation by ID

|  |  |
| --- | --- |
| This command returns information on an Instant Recovery to Microsoft Azure operation by its ID.  |  | | --- | | $recovery = Get-VBRAzureInstantRecovery -Id "d1d2a50e-8052-498f-826b-e5c86f30ed5a" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Information on Microsoft Azure VM

|  |  |
| --- | --- |
| This example shows how to get information on Microsoft Azure VM created during Instant Recovery.  |  | | --- | | $recovery = Get-VBRAzureInstantRecovery  $recovery[1].TargetVm  ResourceGroup    : veeam-tech-group  VMName           : veeam-tech-group-azure-small  SubscriptionName : veeam - TECH - VBR - Azure - InstantRestore  VirtualNetwork   : /subscriptions/e3f47c19-6b82-4d2f-9a5d-c1e7b0f34a12/resourceGroups/tech-ir2az-infra-rg01/providers/Microsoft.Network/virtualNetworks/tech  VirtualSubnet    : /subscriptions/e3f47c19-6b82-4d2f-9a5d-c1e7b0f34a12/resourceGroups/tech-ir2az-infra-rg01/providers/Microsoft.Network/virtualNetworks/tech/subnets/default  ApplianceSubnet  : /subscriptions/e3f47c19-6b82-4d2f-9a5d-c1e7b0f34a12/resourceGroups/tech-ir2az-infra-rg01/providers/Microsoft.Network/virtualNetworks/tech/subnets/default |  Perform the following steps:   1. Run the Get-VBRAzureInstantRecovery cmdlet. Save the result to the $recovery parameter.   The cmdlet will return an array of Instant Recovery to Microsoft Azure operations. Mind the ordinal number of the session (in our example, it is the second restore session in the array).   1. Provide the TargetVm property for the $recovery[1] variable. |

Related Commands

[Start-VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md)



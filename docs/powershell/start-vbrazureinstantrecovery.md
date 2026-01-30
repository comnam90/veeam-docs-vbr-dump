---
title: "Start-VBRAzureInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrazureinstantrecovery.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Start-VBRAzureInstantRecovery


Short Description

Starts Instant Recovery to Microsoft Azure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRAzureInstantRecovery -RestorePoint <COib> -Subscription <VBRAzureSubscription> -Location <VBRAzureLocation> -VmSize <VBRAzureVMSize> -VirtualNetwork <VBRAzureVirtualNetwork> -VirtualSubnet <VBRAzureNetworkSubnet> -ApplianceSubnet <VBRAzureNetworkSubnet> [-VmName <string>] [-DiskConfigurations <VBRAzureDiskConfiguration[]>] [-Tags <VBRAzureTag[]>] [-ResourceGroup <VBRAzureResourceGroup>] [-NewResourceGroupName <string>] [-ApplianceStorageAccount <VBRAzureStorageAccount>] [-NetworkSecurityGroup <VBRNetworkSecurityGroup>] [-AllocatePublicIP] [-VerifyVMBoot] [-Reason <string>] [-RunAsync][<CommonParameters>] |

Detailed Description

This cmdlet starts Instant Recovery to Microsoft Azure. For the list of workload types that you can restore, see in the [Instant Recovery to Microsoft Azure](https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_to_azure.html?ver=13) section in the Veeam Backup & Replication User Guide.

The recovered VM runs from a backup and does not provide a fully functioning service. You need to finalize the successful instant recovery by one of the following steps:

* Migrate the recovered VM to the production. To do this, run the [Start-VBRAzureInstantRecoveryMigration](start-vbrazureinstantrecoverymigration.md) cmdlet.
* Remove the recovered VM. You can stop publishing the recovered VM and discard the changes made to it while it was running from backup. To do this, run the [Stop-VBRAzureInstantRecovery](stop-vbrazureinstantrecovery.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point to which you want to recover the workload. | Accepts the COib object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True |
| Subscription | Specifies the Microsoft Azure subscription. The cmdlet will recover the workload to this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To get this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | False |
| Location | Specifies a geographic region to which you want to place the recovered workloads. | Accepts the VBRAzureLocation object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | True | Named | False |
| VmSize | Specifies the Microsoft Azure VM configuration. The recovered workload will use this configuration template. | Accepts the [VBRAzureVMSize](vbrazurevmsize.md) object. To get this object, run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. | True | Named | False |
| VirtualNetwork | Specifies the Microsoft Azure virtual network. The recovered workload will be connected to this network. | Accepts the [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) object. To get this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | True | Named | False |
| VirtualSubnet | Specifies the Microsoft Azure virtual subnet. The recovered workload will be connected to this subnet.  Note: It is recommended to use separate subnets for the VirtualSubnet and ApplianceSubnet parameters, otherwise some OSes may not boot. | Accepts the [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) object. To get this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | True | Named | False |
| ApplianceSubnet | Specifies the subnet where the cmdlet deploys the helper appliance for the recovered workload.  Note: It is recommended to use separate subnets for the VirtualSubnet and ApplianceSubnet parameters, otherwise some OSes may not boot. | Accepts the [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) object. To get this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | True | Named | False |
| VmName | Specifies the VM name. The recovered workload will have this name.  If you do not specify a new name, the restored VM will have the original name. | String | False | Named | False |
| DiskConfigurations | Specifies the Microsoft Azure VM disk type. The cmdlet will attach disks of this type to the recovered workload.  Default: Premium SSD. | Accepts the [VBRAzureDiskConfiguration[]](vbrazurediskconfiguration.md) object. To create this object, run the [New-VBRAzureDiskConfiguration](new-vbrazurediskconfiguration.md) cmdlet. | False | Named | False |
| Tags | Specifies tags that you want to assign to the recovered workloads. | Accepts the VBRAzureTag[] object. To create this object, run the [New-VBRAzureTag](new-vbrazuretag.md) cmdlet. | False | Named | False |
| ResourceGroup | Specifies the resource group. The recovered workload will use this restore group.  If you skip this parameter, the cmdlet will need to create a new resource group. Use the NewResourceGroupName parameter to create a new resource group. | Accepts the [VBRAzureResourceGroup](vbrazureresourcegroup.md) object. To get this object, run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. | False | Named | False |
| NewResourceGroupName | Specifies the name of a new resource group. The cmdlet will create a new resource group with this name.  If you skip this parameter, use the ResourceGroup parameter to specify an existing resource group. | String | False | Named | False |
| ApplianceStorageAccount | Specifies the storage account through which the recovered workload will communicated with the helper appliance. | Accepts the VBRAzureStorageAccount object. To get this object, run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. | False | Named | False |
| NetworkSecurityGroup | Specifies the security group for the recovered workload. | Accepts the VBRNetworkSecurityGroup object. To get this object, run the [Get-VBRAzureNetworkSecurityGroup](get-vbrazurenetworksecuritygroup.md) cmdlet. | False | Named | False |
| AllocatePublicIP | Defines that the cmdlet will assign a public IP to the recovered workload. | SwitchParameter | False | Named | False |
| VerifyVMBoot | Defines that Veeam Backup & Replication checks if the recovered workload boots successfully.  Veeam Backup & Replication considers recovery as successful after receiving a response from the recovered workload. If the response is not received, Veeam Backup & Replication sends a warning in the recovery session. | SwitchParameter | False | Named | False |
| Reason | Specifies a restore reason. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureInstantRecovery](vbrazureinstantrecovery.md)

Examples

This example shows how to start Instant Recovery to Microsoft Azure.

|  |
| --- |
| $point = Get-VBRBackup -Name "Tech VM" | Get-VBRRestorePoint -Name "backup-azure-win16-g1" | Sort-Object –Property CreationTime –Descending | Select-Object -First 1  $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Tech.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "swedencentral"  $vmSize = Get-VBRAzureVMSize -Subscription $subscription -Location $location -Name "Standard\_F4s\_v2"  $virtualNetwork = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name tech\* -Location $location  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $virtualNetwork -Name "default"  $group = Get-VBRAzureResourceGroup -Subscription $subscription -Name "tech-ts-group" -Location $location  $session = Start-VBRAzureInstantRecovery -RestorePoint $point -Subscription $subscription -Location $location -VmSize $vmSize -VirtualNetwork $virtualNetwork -VirtualSubnet $subnet -ApplianceSubnet $subnet -VmName "tech-recovered-VM" -ResourceGroup $group -RunAsync |

Perform the following steps:

1. Get the restore point:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value.
2. Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value.
3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter.
4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value.

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable.
3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $location variable.
4. Run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Specify the Name parameter value. Save it to the $vmSize variable.
5. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Set the $location variable as the Location parameter value. Save it to the $virtualNetwork variable.
6. Run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. Set the $virtualNetwork variable as the Network parameter value. Specify the Name parameter value. Save it to the $subnet variable.
7. Run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Specify the Name parameter value. Save it to the $group variable.
8. Run the Start-VBRAzureInstantRecovery cmdlet. Specify the following settings:

* Set the $point variable as the RestorePoint parameter value.
* Set the $subscription variable as the Subscription parameter value.
* Set the $location variable as the Location parameter value.
* Set the $vmSize variable as the VmSize parameter value.
* Set the $virtualNetwork variable as the VirtualNetwork parameter value.
* Set the $subnet variable as the VirtualSubnet parameter value.
* Set the $subnet variable as the ApplianceSubnet parameter value.
* Specify the VmName parameter value.
* Set the $group variable as the ResourceGroup parameter value.
* Specify the RunAsync parameter value.
* Save the result to the $session variable.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)
* [Get-VBRAzureVMSize](get-vbrazurevmsize.md)
* [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md)
* [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md)
* [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md)



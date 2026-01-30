---
title: "Add-VBRAzureRestoreProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazurerestoreproxy.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAzureRestoreProxy


Short Description

Creates a proxy appliance used for restoring workloads to Microsoft Azure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureRestoreProxy -Name <string> -Description <string> -MaxConcurrentTasks <int> -CredentialsId <guid> -TrafficPort <int> -Subscription <VBRAzureSubscription> -Location <VBRAzureLocation> -VmSize <VBRAzureVMSize> -StorageAccount <VBRAzureStorageAccount> -ResourceGroup <VBRAzureResourceGroup> -DnsNameLabel <string> -VirtualNetwork <VBRAzureVirtualNetwork> -VirtualSubnet <VBRAzureNetworkSubnet> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a Windows-based proxy appliance. You can use this proxy appliance to restore Windows-based and Linux-based workloads to Microsoft Azure.

|  |
| --- |
| Note |
| When you specify a name of a restore proxy appliance, consider the following requirements:   * The name must not be longer than 15 characters. * The name must contain only alphanumeric characters and hyphens. * The name must start with a letter and end with a letter or number. * The name must not contain only numeric characters. * The name must not contain special characters: `!@#$%^&\*()+=\_[]{}\;:.'",<>/?. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name for the restore proxy appliance. | String | True | Named | True |
| Description | Specifies a description for the restore proxy appliance. | String | True | Named | True |
| MaxConcurrentTasks | Specifies a number of concurrent tasks that the Azure restore proxy appliance must handle in parallel.  Recommended value: 4 tasks. | Int | True | Named | True |
| CredentialsId | Specifies credentials of a user that will be assigned the Local Administrator permissions on the restore proxy appliance.  Note:   * You cannot use reserved names such as 'administrator', 'admin', 'user', 'abc@123', 'P@$$w0rd' and so on as a user name and password of the local administrator account. * You must specify the user name without a domain or Microsoft Azure machine name. * The password must be at least 8 characters long, and must contain at least 1 uppercase character, 1 lowercase character, 1 numeric character and 1 special character. | Guid | True | Named | True |
| TrafficPort | Specifies a port number. The cmdlet will use this port to control components installed on the restore proxy appliance and transport workload disks data to Blob storage.  Default: 443. | Int | True | Named | True |
| Subscription | Specifies the Microsoft Azure subscription whose resources you want to use to deploy the restore proxy appliance. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True |
| Location | Specifies the geographic region to which you want to place the restore proxy appliance. | Accepts the [VBRAzureLocation](vbrazurelocation.md) object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | True | Named | True |
| VmSize | Specifies the size for the proxy appliance VM. | Accepts the VBRAzureVMSize object. To create this object, run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. | True | Named | True |
| StorageAccount | Specifies the storage account you want to use to deploy the restore proxy appliance VM. | Accepts the [VBRAzureStorageAccount](vbrazurestorageaccount.md) object. To get this object, run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. | True | Named | True |
| ResourceGroup | Specifies the resource group to which the proxy appliance must be placed. | Accepts the [VBRAzureResourceGroup](vbrazureresourcegroup.md) object. To get this object, run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. | True | Named | True |
| DnsNameLabel | Specifies a DNS name label for the public IP that will be created. | String | True | Named | True |
| VirtualNetwork | Specifies a virtual network. | Accept the [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) object. To get this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | True | Named | True |
| VirtualSubnet | Specifies the virtual network subnet to which you want to connect the restore proxy appliance. | Accepts the [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) object. To create this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | True | Named | True |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureRestoreProxy](vbrazurerestoreproxy.md)

Examples

Creating Microsoft Azure Restore Proxy Appliance

This example shows how to create a restore proxy appliance for restoring backups to Microsoft Azure VMs

|  |
| --- |
| $account = Get-VBRAzureAccount -Name "azcomputeaccount"  $subscription = Get-VBRAzureSubscription -Account $account -Name "ContosoProd"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "westeurope"  $rg = Get-VBRAzureResourceGroup -Subscription $subscription -Name "azprx01-rg"  $storage = Get-VBRAzureStorageAccount -Subscription $subscription -Name "veeamstorage01"  $vnet = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "veeamvnet"  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $vnet -Name "default"  $vmSize = Get-VBRAzureVMSize -Subscription $subscription -Location $location -Name "Standard\_F4s\_v2"  $creds = Add-VBRCredentials -Type "Windows" -User "veeamadmin" -Password "P@ssw0rd!"  Add-VBRAzureRestoreProxy -Name "azprx01" -Description "Azure restore proxy appliance" -MaxConcurrentTasks 4 -CredentialsId $creds.Id -TrafficPort 443 -Subscription $subscription -Location $location -VmSize $vmSize -StorageAccount $storage -ResourceGroup $rg -DnsNameLabel "azprx01" -VirtualNetwork $vnet -VirtualSubnet $subnet -Wait |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Specify the Account and Name parameters value. Save the result to the $subscription variable.
3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Specify the Subscription and Name parameters values. Save the result to the $location variable.
4. Run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. Specify the Subscription and Name parameters values. Save the result to the $rg variable.
5. Run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. Specify the ResourceGroup and Name parameters values. Save the result to the $storage variable.
6. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Specify the ResourceGroup and Name parameters values. Save the result to the $vnet variable.
7. Run the [Get-VBRAzureNetworkSubnet](get-vbrazureresourcegroup.md) cmdlet. Specify the VirtualNetwork and Name parameters values. Save the result to the $subnet variable.
8. Run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. Specify the Subscription, Location and Name parameters values. Save the result to the $vmSize variable.
9. Run the [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. Specify the Type, User, and Password parameter values. Save the result to the $cred variable.
10. Run the Add-VBRAzureRestoreProxy cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Specify the Description parameter value.
* Specify the MaxConcurrentTasks parameter value.
* Set the $creds.Id as the CredentialsId parameter value.
* Specify the TrafficPort parameter value.
* Set the $subscription as the Subscription parameter value.
* Set the $location as the Location parameter value.
* Set the $vmSize as the VmSize parameter value.
* Set the $storage as the StorageAccount parameter value.
* Set the $rg as the ResourceGroup parameter value.
* Specify the DnsNameLabel parameter value.
* Set the $vnet as the VirtualNetwork parameter value.
* Set the $subnet as the VirtualSubnet parameter value.
* Provide the Wait parameter.

Related Commands

* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)
* [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md)
* [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md)
* [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md)
* [Get-VBRAzureNetworkSubnet](get-vbrazureresourcegroup.md)
* [Get-VBRAzureVMSize](get-vbrazurevmsize.md)



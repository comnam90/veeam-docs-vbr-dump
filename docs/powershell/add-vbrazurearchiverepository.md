---
title: "Add-VBRAzureArchiveRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazurearchiverepository.html"
last_updated: "9/2/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAzureArchiveRepository

In this article

Short Description

Adds Azure Archive repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureArchiveRepository -Connection <VBRAzureBlobConnection> -AzureBlobFolder <VBRAzureBlobFolder> [-EnableBackupImmutability] [-AzureProxySpec <VBRAzureComputeProxyAppliance>] [-Name <String>] [-Description <String>] [-UseInstantRetrieval] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet adds Azure Archive repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with an Azure Archive repository that you want to add to the backup infrastructure. | Accepts the VBRAzureBlobConnection object. To create this object, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet and set the ArchiveTier property as the ServiceType parameter value. | True | Named | True |
| AzureBlobFolder | Specifies an Azure Blob folder. Veeam Backup & Replication will move backup files into this folder. | Accepts the VBRAzureBlobFolder object. To create this object, run the [New-VBRAzureBlobFolder](new-vbrazureblobfolder.md) cmdlet. | True | Named | False |
| EnableBackupImmutability | Defines that the cmdlet will enable the immutability option.  Default: False. | SwitchParameter | False | Named | False |
| AzureProxySpec | Specifies an archiver appliance that transfers data from Azure Blob storage to Azure Archive Storage. | Accepts the VBRAzureComputeProxyAppliance object. To create this object, run the [New-VBRAzureComputeProxyAppliance](new-vbrazurecomputeproxyappliance.md) cmdlet. | False | Named | False |
| Name | Specifies a name of an Azure Archive repository. The cmdlet will add an archive repository with this name. | String | False | Named | False |
| Description | Specifies a description of an Azure Archive repository. The cmdlet will add an archive repository with this description. | String | False | Named | False |
| UseInstantRetrieval | Defines that the cmdlet will create a repository where data blocks are marked with the cool access tier.  Note: If you do not provide the UseInstantRetrieval parameter, the cmdlet will create a repository where blocks are marked as the archive access tier.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureArchiveRepository](vbrazurearchiverepository.md)

Examples

Adding Azure Archive Repository

This example shows how to add the Azure Archive repository to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Azure\_Blob"  $connection = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType ArchiveTier  $container = Get-VBRAzureBlobContainer -Connection $connection -Name "container01"  $folder = Get-VBRAzureBlobFolder -Container $container -Connection $connection -Name "folder02"  $subscriptaccount = Get-VBRAzureAccount  $subscription = Get-VBRAzureSubscription -Account $subscriptaccount  $location = Get-VBRAzureLocation -Subscription $subscription  $vmsize = Get-VBRAzureVMSize -Subscription $subscription -Location $location  $network = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "VeeamInternalNetwork"  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $network -Name "VeeamInternalSubnet"  $rg = Get-VBRAzureResourceGroup -Subscription $subscription -Name "VeeamResourceGroup"  $proxy = New-VBRAzureComputeProxyAppliance -VMSize $vmsize -Network $network -Subnet $subnet -ResourceGroup $rg -RedirectorPort 443  Add-VBRAzureArchiveRepository -Connection $connection -AzureBlobFolder $folder -AzureProxySpec $proxy -Name "MyAzureArchive" |

Perform the following steps:

1. Specify Azure connection settings:

* Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
* Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable.

1. Specify object storage settings:

* Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Set the $connection variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $container variable.
* Run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. Set the $container variable as the Container parameter value. Set the $connection variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $folder variable.

1. Define the Azure proxy settings:

* Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Save the result to the $subscriptaccount variable.
* Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $subscriptaccount variable as the Account parameter value. Save the result to the $subscription variable.
* Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable the Subscription parameter value. Save the result to the $location variable.
* Run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save the result to the $vmsize variable.
* Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $network variable.
* Run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. Set the $network variable as the Network parameter value. Specify the Name parameter values. Save the result to the $subnet variable.
* Run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $rg variable.
* Run the [New-VBRAzureComputeProxyAppliance](new-vbrazurecomputeproxyappliance.md) cmdlet. Set the $vmsize variable as the VMSize parameter value. Set the $network variable as the Network parameter value. Set the $subnet variable as the Subnet parameter value. Set the $rg variable as the ResourceGroup parameter value. Specify the RedirectorPort parameter value. Save the result to the $proxy variable.

1. Run the Add-VBRAzureArchiveRepository cmdlet. Specify the following settings:

* Set the $connection variable as the Connection parameter value.
* Set the $folder variable as the AzureBlobFolder parameter value.
* Set the $proxy variable as the AzureProxySpec parameter value.

* Specify the Name parameter value.

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)
* [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md)
* [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)
* [Get-VBRAzureVMSize](get-vbrazurevmsize.md)
* [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md)
* [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md)
* [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md)
* [New-VBRAzureComputeProxyAppliance](new-vbrazurecomputeproxyappliance.md)

Page updated 9/2/2024

Page content applies to build 13.0.1.1071

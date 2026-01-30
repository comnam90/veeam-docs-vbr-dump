---
title: "Start-VBRVMRestoreToAzure"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvmrestoretoazure.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# Start-VBRVMRestoreToAzure


Short Description

Restores VM backups to Microsoft Azure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore to Azure with the following deployment models.

* Microsoft Azure Resource Manager
* Microsoft Azure Stack

|  |
| --- |
| Start-VBRVMRestoreToAzure -RestorePoint <COib> -Subscription <VBRAzureSubscription> -VmSize <VBRAzureVMSize> -VirtualNetwork <VBRAzureVirtualNetwork> -VirtualSubnet <VBRAzureNetworkSubnet> [-ResourceGroup <VBRAzureResourceGroup>] [-NewResourceGroupName <string>] [-StorageAccount <VBRAzureStorageAccount>] [-Location <VBRAzureLocation>] [-DisksToExclude <string[]>] [-DiskConfigurations <VBRAzureDiskConfiguration[]>] [-VmName <string>] [-Reason <string>] [-GatewayServer <CHost>] [-Credentials <CCredentials>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction {ConnectToIsolatedNetwork | AbortRecovery}] [-VirusIsolatedNetwork <VBRAzureVirtualNetwork>] [-VirusIsolatedNetworkSubnet <VBRAzureNetworkSubnet>] [-NetworkSecurityGroup <VBRNetworkSecurityGroup>] [-Wait] [-AllocatePublicIP] [-ShutdownVM] [-StorageType {Managed | Unmanaged}]  [<CommonParameters>] |

* For Microsoft Azure Classic deployment model.

|  |
| --- |
| [-StorageAccount <VBRAzureStorageAccount>] [-Location <VBRAzureLocation>] [-DisksToExclude <string[]>] [-DiskConfigurations <VBRAzureDiskConfiguration[]>] [-VmName <string>] [-CloudService <VBRAzureCloudService>] [-DNSName <string>] [-Endpoint <uint16>] [-VirtualNetwork <VBRAzureVirtualNetwork>] [-VirtualSubnet <VBRAzureNetworkSubnet>] [-Reason <string>] [-GatewayServer <CHost>] [-Credentials <CCredentials>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction {ConnectToIsolatedNetwork | AbortRecovery}] [-VirusIsolatedNetwork <VBRAzureVirtualNetwork>] [-VirusIsolatedNetworkSubnet <VBRAzureNetworkSubnet>] [-NetworkSecurityGroup <VBRNetworkSecurityGroup>] [-Wait] [-AllocatePublicIP] [-ShutdownVM] [-StorageType {Managed | Unmanaged}]  [<CommonParameters>] |

Detailed Description

This cmdlet restores VM backups to Microsoft Azure. You can restore the data to the following types of Microsoft Azure deployment models:

* Microsoft Azure Resource Manager
* Microsoft Azure Stack
* For Microsoft Azure Classic

|  |
| --- |
| Important |
| You must select the Microsoft Azure configuration options that supports the VM you restore. For example, if you restore a VM that has 4 disks, select an Azure VM configuration option that supports 4 or more disks. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the backup you want to restore to Microsoft Azure. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Subscription | Specifies the Microsoft Azure subscription. The cmdlet will restore the backup to this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To get this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | False |
| VmSize | Specifies the Microsoft Azure VM configuration option. The VM will use this configuration template. | Accepts the [VBRAzureVMSize](vbrazurevmsize.md) object. To get this object, run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. | True | Named | False |
| StorageAccount | Specifies the Microsoft Azure storage account. The restored VM will use this storage account.  Note: This parameter is not required if the StorageType parameter is set to Managed. If you do not specify the StorageAccount parameter, you must specify the Location parameter. | Accepts the [VBRAzureStorageAccount](vbrazurestorageaccount.md) object. To get this object, run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. | False | Named | False |
| VirtualNetwork | Specifies the Microsoft Azure virtual network. The restored VM will be connected to this network. | Accepts the [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) object. To get this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | For Resource Manager model: True  For Classic model: False | Named | False |
| VirtualSubnet | Specifies the Microsoft Azure virtual subnet. The restored VM will be connected to this subnet. | Accepts the [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) object. To get this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | For Resource Manager model: True  For Classic model: False | Named | False |
| ResourceGroup | For Microsoft Azure Resource Manager accounts.  Specifies the Microsoft Azure resource group. The restored VM will use this restore group.  If you skip this parameter, the cmdlet will need to create a new resource group. Use the NewResourceGroupName parameter to create a new resource group. The new resource group is created with default resources. | Accepts the [VBRAzureResourceGroup](vbrazureresourcegroup.md) object. To get this object, run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. | False | Named | False |
| NewResourceGroupName | For Microsoft Azure Resource Manager deployment models.  Specifies the name of a new resource group. The cmdlet will create a new resource group with this name.  If you skip this parameter, use the ResourceGroup parameter to specify an existing resource group. | String | False | Named | False |
| Location | Specifies a geographic location of Microsoft Azure datacenters. The cmdletwill restore a VM to this location. | Accepts the [VBRAzureLocation](vbrazurelocation.md) object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | False | Named | False |
| DisksToExclude | Specifies the array of VM disk file names. Use this parameter to specify the VM disks that you want to exclude. The cmdlet will not restore these disks. | String[] | False | Named | False |
| VmName | Specifies the VM name. The restored VM will have this name.  If you do not specify a new name, the restored VM will have it's original name. | String | False | Named | False |
| DiskConfigurations | Specifies the Azure VM disk type. The cmdlet will attach disks of this type to the restored VM.  If you do not specify this parameter, the cmdlet will restore all disks as Standard HDD. | Accepts the [VBRAzureDiskConfiguration](vbrazurediskconfiguration.md) object. To create this object, run the [New-VBRAzureDiskConfiguration](new-vbrazurediskconfiguration.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for performing restore. | String | False | Named | False |
| GatewayServer | Specifies the proxy server. The restore process will use this server to transfer the VM data to the Microsoft Azure datacenter.  If you skip this parameter, the restore process will use Veeam backup server as a proxy server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Credentials | For restoring backups located on a network shared folder.  Specifies the credentials to authenticate with the network shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| EnableAntivirusScan | Enables the secure restore option. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Defines that the antivirus will continue VMs scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies secure restore action when the virus threat is detected.   * ConnectToIsolatedNetwork - use this option if you want to restore a machine to the isolated network. * AbortRecovery - use this option if you want to cancel the restore session. | VBRAzureVirusDetectionAction | False | Named | False |
| VirusIsolatedNetwork | Specifies the Azure virtual network. Veeam Backup & Replication will restore the infected VM to the selected network. | Accepts the [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) object. To get this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | False | Named | False |
| VirusIsolatedNetworkSubnet | Specifies the Azure virtual network subnet. Veeam Backup & Replication will restore the infected VM to the selected network. | Accepts the [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) object. To get this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | False | Named | False |
| NetworkSecurityGroup | Specifies a security group for the restored VM. | Accepts the VBRNetworkSecurityGroup object. | False | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |
| AllocatePublicIP | Defines that the cmdlet will assign a public IP to the restored VM.  If you provide this parameter, Veeam Backup & Replication will assign a public IP to it.  Otherwise, the restored VM will remain without the public IP. | SwitchParameter | False | Named | False |
| ShutdownVM | Defines that the cmdlet will power on the restored VM after the restore is complete.  If you do not provide this parameter, the restored VM will remain powered on. | SwitchParameter | False | Named | False |
| StorageType | Specifies a type of Microsoft Azure disks. You can specify either of the following disk types:   * Managed * Unmanaged | VBRAzureStorageType | False | Named | False |
| CloudService | For Microsoft Azure Classic accounts.  Specifies the existing cloud service. The restored VM will be added to this cloud service.  If you skip this parameter, the cmdlet will create a new cloud service for the restored VM. Use the DNSName parameter to set the name for the new cloud service. | Accepts the [VBRAzureCloudService](vbrazurecloudservice.md) object. To get this object, run the [Get-VBRAzureCloudService](get-vbrazurecloudservice.md) cmdlet. | False | Named | False |
| DNSName | For Microsoft Azure Classic deployment model.  Specifies the name of the new cloud service.  If you skip this parameter, use the CloudService parameter to place the restored VM to an existing cloud service. | String | False | Named | False |
| Endpoint | For Microsoft Azure Classic accounts.  Specifies the port number. This port will be used to connect to the restored VM.  If you skip this parameter, the cmdlet will use the default port numbers:  For Windows VMs: 3389.  For Linux VMs: 22. | UInt16 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureRestoreSession](vbrazurerestoresession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring VM to Microsoft Azure for Resource Manager Deployment Model

|  |  |
| --- | --- |
| This example shows how to restore a VM to Microsoft Azure for the Resource Manager deployment model.  |  | | --- | | $restorepoint = Get-VBRBackup -Name "MSExchange Backup" | Get-VBRRestorePoint -Name "MSExchange02" | Sort-Object CreationTime -Descending | Select -First 1  $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $storageaccount = Get-VBRAzureStorageAccount -Subscription $subscription -Name "VeeamDirectRestore2AzureStorage"  $location = Get-VBRAzureLocation -Subscription $subscription -Name australiaeast  $vmsize = Get-VBRAzureVMSize -Subscription $subscription -Location $location -Name Standard\_G3  $network = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "VeeamInternalNetwork"  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $network -Name "VeeamInternalSubnet"  $resourcegroup = Get-VBRAzureResourceGroup -Subscription $subscription -Name "VeeamResourceGroup"  Start-VBRVMRestoreToAzure -RestorePoint $restorepoint -Subscription $subscription -StorageAccount $storageaccount -VmSize $vmsize -VirtualNetwork $network -VirtualSubnet $subnet -ResourceGroup $resourcegroup -VmName CRM\_db\_restored2Azure -Reason "Back up CRM\_db to Microsoft Azure" |  Perform the following steps:   1. Get the restore point of the VM that you want to restore:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the Sort-Object cmdlet and specify the CreationTime parameter value. * Pipe the cmdlet output to the Select cmdlet. Specify the First parameter value. * Save the result to the $restorepoint variable.  1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save the subscription to the $subscription variable. 3. Run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $storageaccount variable. 4. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $location variable. 5. Run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Specify the Name parameter value. Save it to the $vmsize variable. 6. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $network variable. 7. Run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. Set the $network variable as the Network parameter value. Specify the Name parameter value. Save the result to the $subnet variable. 8. Run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $resourcegroup variable. 9. Run the Start-VBRVMRestoreToAzure cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $subscription variable as the Subscription parameter value. * Set the $storageaccount variable as the StorageAccount parameter value. * Set the $vmsize variable as the VmSize parameter value. * Set the $network variable as the VirtualNetwork parameter value. * Set the $subnet variable as the VirtualSubnet parameter value. * Set the $resourcegroup variable as the ResourceGroup parameter value. * Specify the VmName and the Reason parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring VM to Microsoft Azure Classic Deployment Model

|  |  |
| --- | --- |
| This example shows how to restore a VM to a Classic account.  |  | | --- | | $restorepoint = Get-VBRBackup -Name "MSExchange Backup" | Get-VBRRestorePoint -Name "MSExchange02" | Sort-Object CreationTime -Descending | Select -First 1  $account = Get-VBRAzureAccount -Type Classic -Name "RestoreToAzure@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $storageaccount = Get-VBRAzureStorageAccount -Subscription $subscription -Name "VeeamDirectRestore2AzureStorage"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "Classic Central US"  $vmsize = Get-VBRAzureVMSize -Subscription $subscription -Location $location -Name Standard\_G3  Start-VBRVMRestoreToAzure -RestorePoint $restorepoint -Subscription $subscription -StorageAccount $storageaccount -VmSize $vmsize -DNSName "CRM\_db\_Restored\_to\_Azure" -Endpoint 443 -Reason "Back up CRM\_db to Microsoft Azure" |  Perform the following steps:   1. Get the restore point of the VM that you want to restore:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the Sort-Object cmdlet and specify the CreationTime parameter value. * Pipe the cmdlet output to the Select cmdlet. Specify the First parameter value. * Save the result to the $restorepoint variable.  1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the Classic value as the Type parameter value. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save the subscription to the $subscription variable. 3. Run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $storageaccount variable. 4. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $location variable. 5. Run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Specify the Name parameter value. Save it to the $vmsize variable. 6. Run the Start-VBRVMRestoreToAzure cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $subscription variable as the Subscription parameter value. * Set the $storageaccount variable as the StorageAccount parameter value. * Set the $vmsize variable as the VmSize parameter value. * Specify the DNSName parameter value. * Specify the Endpoint parameter value. * Specify the Reason parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring VM Using Proxy Server

|  |  |
| --- | --- |
| This example shows how to start restore using a proxy server.  |  | | --- | | $restorepoint = Get-VBRBackup -Name "MSExchange Backup" | Get-VBRRestorePoint -Name "MSExchange02" | Sort-Object CreationTime -Descending | Select -First 1  $account = Get-VBRAzureAccount -Type Classic -Name "RestoreToAzure@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $storageaccount = Get-VBRAzureStorageAccount -Subscription $subscription -Name "VeeamDirectRestore2AzureStorage"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "Classic Central US"  $vmsize = Get-VBRAzureVMSize -Subscription $subscription -Location $location -Name Standard\_G3  $network = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "VeeamInternalNetwork"  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $network -Name "VeeamInternalSubnet"  $resourcegroup = Get-VBRAzureResourceGroup -Subscription $subscription -Name "VeeamResourceGroup"  $proxy = Get-VBRServer -Name "azureproxy.cloudapp.net"  Start-VBRVMRestoreToAzure -RestorePoint $restorepoint -Subscription $subscription -StorageAccount $storageaccount -VmSize $vmsize -VirtualNetwork $network -VirtualSubnet $subnet -ResourceGroup $resourcegroup -VmName CRM\_db\_restored2Azure -Reason "Back up CRM\_db to Microsoft Azure" -GatewayServer $proxy |  Perform the following steps:   1. Get the restore point of the VM that you want to restore:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the Sort-Object cmdlet and specify the CreationTime parameter value. * Pipe the cmdlet output to the Select cmdlet. Specify the First parameter value. * Save the result to the $restorepoint variable.  1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the Classic value as the Type parameter value. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save the subscription to the $subscription variable. 3. Run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $storageaccount variable. 4. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $location variable. 5. Run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Specify the Name parameter value. Save it to the $vmsize variable. 6. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $network variable. 7. Run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. Set the $network variable as the Network parameter value. Specify the Name parameter value. Save the result to the $subnet variable. 8. Run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $resourcegroup variable. 9. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 10. Run the Start-VBRVMRestoreToAzure cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $subscription variable as the Subscription parameter value. * Set the $storageaccount variable as the StorageAccount parameter value. * Set the $vmsize variable as the VmSize parameter value.  * Set the $network variable as the VirtualNetwork parameter value. * Set the $subnet variable as the VirtualSubnet parameter value. * Set the $resourcegroup variable as the ResourceGroup parameter value.  * Specify the VmName and the Reason parameter values. * Set the $proxy variable as the GatewayServer parameter value. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md)
* [Get-VBRAzureVMSize](get-vbrazurevmsize.md)
* [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md)
* [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRAzureCloudService](get-vbrazurecloudservice.md)



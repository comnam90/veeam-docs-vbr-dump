---
title: "Restore to Microsoft Azure"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/microsoft_azure.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Restore to Microsoft Azure


To use the cmdlets in this section, you must have the Microsoft Azure PowerShell Module installed on your machine. You can install the Microsoft Azure PowerShell Module with the following options:

The module is installed when you add Microsoft Azure account to Veeam Backup & Replication using the Veeam Backup & Replication console

If you add Microsoft Azure accounts to Veeam Backup & Replication using PowerShell, you must first install the Microsoft Azure PowerShell Module. You can find the distribute at the following location: C:\Program Files\Veeam\Backup and Replication\Console\azure-powershell.5.1.1.msi

You can use the cmdlet in this topic to perform the following operations.

| Cmlet | Operation |
| --- | --- |
| [Get-VBRAzureSubscription](get-vbrazuresubscription.md) | Returns subscriptions associated with a Microsoft Azure account. |
| [Get-VBRAzureCloudService](get-vbrazurecloudservice.md) | Returns Microsoft Azure cloud services available for a subscription. |
| [Get-VBRAzureLocation](get-vbrazurelocation.md) | Returns geographic locations of Microsoft Azure datacenters available for a subscription. |
| [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) | Returns Microsoft Azure resource groups available for a subscription. |
| [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) | Returns Microsoft Azure storage accounts available for a subscription. |
| [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) | Returns Microsoft Azure virtual networks available for a subscription. |
| [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) | Returns Microsoft Azure virtual network subnets available for a subscription. |
| [Get-VBRAzureNetworkSecurityGroup](get-vbrazurenetworksecuritygroup.md) | Returns Microsoft Azure security groups. |
| [Get-VBRAzureVMSize](get-vbrazurevmsize.md) | Returns Microsoft Azure VM configuration options available for a subscription. |
| [New-VBRAzureDiskConfiguration](new-vbrazurediskconfiguration.md) | Defines Azure VM disk types. |
| [New-VBRAzureLinuxRestoreAppliance](new-vbrazurelinuxrestoreappliance.md) | Creates helper appliances for restoring Linux VMs to Microsoft Azure. |
| [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md) | Returns helper appliances for restoring Linux VMs to Microsoft Azure. |
| [Set-VBRAzureLinuxRestoreAppliance](set-vbrazurelinuxrestoreappliance.md) | Modifies helper appliances for restoring Linux VMs to Microsoft Azure. |
| [Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md) | Deploys or removes helper appliances for restoring Linux VMs to Microsoft Azure. |
| [Add-VBRAzureRestoreProxy](add-vbrazurerestoreproxy.md) | Creates a restore proxy appliance used for restoring workloads to Microsoft Azure |
| [Get-VBRAzureRestoreProxy](get-vbrazurerestoreproxy.md) | Returns a restore proxy appliance used for restoring workloads to Microsoft Azure |
| [Remove-VBRAzureRestoreProxy](remove-vbrazurerestoreproxy.md) | Removes a restore proxy appliance from the backup infrastructure. |
| [Get-VBRAzureApplianceSession](get-vbrazureappliancesession.md) | Returns statuses of deployment sessions for helper restore appliance. |
| [Start-VBRVMRestoreToAzure](start-vbrvmrestoretoazure.md) | Restores VM backups to Microsoft Azure. |
| [Get-VBRAzureRestoreSession](get-vbrazurerestoresession.md) | Returns VM backup restore to Microsoft Azure sessions. |
| [Stop-VBRVMRestoreToAzure](stop-vbrvmrestoretoazure.md) | Stops running VM backup restore to Microsoft Azure sessions. |



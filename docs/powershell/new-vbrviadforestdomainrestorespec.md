---
title: "New-VBRViADForestDomainRestoreSpec"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrviadforestdomainrestorespec.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRViADForestDomainRestoreSpec


Short Description

Creates a VMware domain restore specification for a Microsoft Active Directory forest restore.

Applies to

Platform: VMware

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| New-VBRViADForestDomainRestoreSpec [-RestorePoint] <VBRADForestDomainRestorePoint> -Credentials <PSCredential> -Server <CHost> -ResourcePool <CViResourcePoolItem> -Datastore <CViDatastoreItem> -Folder <CViFolderItem> -VMName <String> [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRADForestDomainRestoreSpec](vbradforestdomainrestorespec.md) object. This object defines the target settings for restoring a domain controller VM on a VMware host during a Microsoft Active Directory forest restore. Create one specification for each domain controller you want to restore. Use this object with the [Start-VBRADForestRestore](start-vbradforestrestore.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies the domain controller restore point to use for the restore operation. | Accepts the [VBRADForestDomainRestorePoint](vbradforestdomainrestorepoint.md) object. To get this object, run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| Credentials | Specifies the guest OS credentials of the restored domain controller. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. | True | Named | False |
| Server | Specifies the VMware ESXi host on which to restore the domain controller VM. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| ResourcePool | Specifies the resource pool on the target ESXi host where the domain controller VM will be placed. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | True | Named | False |
| Datastore | Specifies the datastore on the target ESXi host where the domain controller VM files will be stored. | Accepts the CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | True | Named | False |
| Folder | Specifies the VM folder in the vCenter Server inventory where the restored domain controller VM will appear. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| VMName | Specifies the name for the restored domain controller VM. The name can contain from 1 to 81 characters. | String | True | Named | False |
| SourceNetwork | Specifies the array of virtual networks connected to the domain controller VM in the source environment. Use this parameter together with the TargetNetwork parameter to configure network mapping. The SourceNetwork and TargetNetwork arrays must contain the same number of networks. Network mapping is required when you restore the domain controller VM to a host other than the original one. | Accepts the [VBRViNetworkInfo](vbrvinetworkinfo.md)[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | Specifies the array of virtual networks connected to the target VMware host that the domain controller VM will be mapped to. Use this parameter together with the SourceNetwork parameter to configure network mapping. The SourceNetwork and TargetNetwork arrays must contain the same number of networks. Network mapping is required when you restore the domain controller VM to a host other than the original one. | Accepts the [VBRViNetworkInfo](vbrvinetworkinfo.md)[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestDomainRestoreSpec](vbradforestdomainrestorespec.md) object that defines the target settings for restoring a domain controller VM on a VMware host.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating VMware Domain Restore Specification

|  |  |
| --- | --- |
| This example shows how to create a domain restore specification for a VMware environment.  |  | | --- | | $forest = Get-VBRADForest  $domain = Get-VBRADForestDomain -ADForest $forest  $domainRestorePoint = Get-VBRADForestDomainRestorePoint -Domain $domain  $server = Get-VBRServer -Name "esx01.company.local"  $credentials = Get-Credential  $resourcePool = Find-VBRViResourcePool -Server $server -Name "Resources"  $datastore = Find-VBRViDatastore -Server $server -Name "Datastore01"  $folder = Find-VBRViEntity -Server $server -Name "Discovered virtual machine"  $viSpec = New-VBRViADForestDomainRestoreSpec -RestorePoint $domainRestorePoint[0] -Credentials $credentials -Server $server -ResourcePool $resourcePool -Datastore $datastore -Folder $folder -VMName "DC01-Restored" |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domain variable. 3. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $domainRestorePoint variable. The cmdlet returns an array of restore points (points in time); this example uses the first one ($domainRestorePoint[0]). 4. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $credentials variable. 6. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $resourcePool variable. 7. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $datastore variable. 8. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $folder variable. 9. Run the New-VBRViADForestDomainRestoreSpec cmdlet. Specify the following parameters:  * Set the $domainRestorePoint[0] variable as the RestorePoint parameter value. * Set the $credentials variable as the Credentials parameter value. * Set the $server variable as the Server parameter value. * Set the $resourcePool variable as the ResourcePool parameter value. * Set the $datastore variable as the Datastore parameter value. * Set the $folder variable as the Folder parameter value. * Specify the VMName parameter value.   Save the result to the $viSpec variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating VMware Domain Restore Specification with Network Mapping

|  |  |
| --- | --- |
| This example shows how to create a domain restore specification with network mapping for a VMware environment.  |  | | --- | | $forest = Get-VBRADForest  $domain = Get-VBRADForestDomain -ADForest $forest  $domainRestorePoint = Get-VBRADForestDomainRestorePoint -Domain $domain  $server = Get-VBRServer -Name "esx01.company.local"  $credentials = Get-Credential  $resourcePool = Find-VBRViResourcePool -Server $server -Name "Resources"  $datastore = Find-VBRViDatastore -Server $server -Name "Datastore01"  $folder = Find-VBRViEntity -Server $server -Name "Discovered virtual machine"  $sourceNetwork = Get-VBRViServerNetworkInfo -Server $server | Where-Object { $\_.NetworkName -eq "VM Network" }  $targetNetwork = Get-VBRViServerNetworkInfo -Server $server | Where-Object { $\_.NetworkName -eq "Restore Network" }  $viSpec = New-VBRViADForestDomainRestoreSpec -RestorePoint $domainRestorePoint[0] -Credentials $credentials -Server $server -ResourcePool $resourcePool -Datastore $datastore -Folder $folder -VMName "DC01-Restored" -SourceNetwork $sourceNetwork -TargetNetwork $targetNetwork |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domain variable. 3. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $domainRestorePoint variable. The cmdlet returns an array of restore points (points in time); this example uses the first one ($domainRestorePoint[0]). 4. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $credentials variable. 6. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $resourcePool variable. 7. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $datastore variable. 8. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $folder variable. 9. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Filter the result by the network name. Save the result to the $sourceNetwork variable. 10. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Filter the result by the network name. Save the result to the $targetNetwork variable. 11. Run the New-VBRViADForestDomainRestoreSpec cmdlet. Specify the following parameters:  * Set the $domainRestorePoint[0] variable as the RestorePoint parameter value. * Set the $credentials variable as the Credentials parameter value. * Set the $server variable as the Server parameter value. * Set the $resourcePool variable as the ResourcePool parameter value. * Set the $datastore variable as the Datastore parameter value. * Set the $folder variable as the Folder parameter value. * Specify the VMName parameter value. * Set the $sourceNetwork variable as the SourceNetwork parameter value. * Set the $targetNetwork variable as the TargetNetwork parameter value.   Save the result to the $viSpec variable to use it with other cmdlets. |

Related Commands

* [Get-VBRADForest](get-vbradforest.md)
* [Get-VBRADForestDomain](get-vbradforestdomain.md)
* [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [Start-VBRADForestRestore](start-vbradforestrestore.md)

Page updated 2026-07-28


---
title: "Start-VBRADForestRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbradforestrestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRADForestRestore


Short Description

Starts a Microsoft Active Directory forest restore.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRADForestRestore -RestorePoint <VBRADForestRestorePoint> -DomainRestoreSpec <VBRADForestDomainRestoreSpec[]> [-ReIpRule <VBRADForestReIpRule[]>] [-Reason <String>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore of a Microsoft Active Directory forest. The cmdlet restores domain controllers from a backup to the specified target hosts.

Before starting the restore, create a domain restore specification for each domain controller you want to restore. For VMware environments, run the [New-VBRViADForestDomainRestoreSpec](new-vbrviadforestdomainrestorespec.md) cmdlet. For Hyper-V environments, run the [New-VBRHvADForestDomainRestoreSpec](new-vbrhvadforestdomainrestorespec.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies the restore point for the Microsoft Active Directory forest from which to restore domain controllers. | Accepts the [VBRADForestRestorePoint](vbradforestrestorepoint.md) object. To get this object, run the [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md) cmdlet. | True | Named | False |
| DomainRestoreSpec | Specifies the array of domain restore specifications. Each specification defines the target settings for restoring a domain controller VM. The domain restore specification must contain exactly one root domain. All domain restore specifications must belong to the same Microsoft Active Directory forest as the specified restore point. | Accepts the [VBRADForestDomainRestoreSpec](vbradforestdomainrestorespec.md)[] object. To create this object, run the [New-VBRViADForestDomainRestoreSpec](new-vbrviadforestdomainrestorespec.md) or [New-VBRHvADForestDomainRestoreSpec](new-vbrhvadforestdomainrestorespec.md) cmdlet. | True | Named | False |
| ReIpRule | Specifies the array of re-IP rules for the restore. Use re-IP rules when the domain controllers must be restored to a network with a different IP addressing scheme. | Accepts the [VBRADForestReIpRule](vbradforestreiprule.md)[] object. To create this object, run the [New-VBRADForestReIpRule](new-vbradforestreiprule.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for the restore operation. Veeam Backup & Replication adds this reason to the restore session log. | String | False | Named | False |
| RunAsync | Defines that the cmdlet will run the restore operation asynchronously. The cmdlet returns a session object immediately without waiting for the restore to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestRestoreSession](vbradforestrestoresession.md) object that contains properties of the Microsoft Active Directory forest restore session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Microsoft Active Directory Forest Restore to VMware vSphere

|  |  |
| --- | --- |
| This example shows how to start a Microsoft Active Directory forest restore for a VMware vSphere environment. It restores two domain controllers — one from the root domain and one from a child domain.  |  | | --- | | $forest = Get-VBRADForest  $restorePoint = (Get-VBRADForestRestorePoint -ADForest $forest)[0]  $domains = Get-VBRADForestDomain -ADForest $forest  $server = Get-VBRServer -Name "esx01.company.local"  $credentials = Get-Credential  $resourcePool = Find-VBRViResourcePool -Server $server -Name "Resources"  $datastore = Find-VBRViDatastore -Server $server -Name "Datastore01"  $folder = Find-VBRViEntity -Server $server -Name "Discovered virtual machine"  $rootRestorePoint = (Get-VBRADForestDomainRestorePoint -Domain $domains[0])[0]  $rootSpec = New-VBRViADForestDomainRestoreSpec -RestorePoint $rootRestorePoint -Credentials $credentials -Server $server -ResourcePool $resourcePool -Datastore $datastore -Folder $folder -VMName "DC01-Restored"  $childRestorePoint = (Get-VBRADForestDomainRestorePoint -Domain $domains[1])[0]  $childSpec = New-VBRViADForestDomainRestoreSpec -RestorePoint $childRestorePoint -Credentials $credentials -Server $server -ResourcePool $resourcePool -Datastore $datastore -Folder $folder -VMName "DC02-Restored"  $restore = Start-VBRADForestRestore -RestorePoint $restorePoint -DomainRestoreSpec @($rootSpec, $childSpec) -RunAsync -Reason "Disaster recovery" |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md) cmdlet. Set the $forest variable as the ADForest parameter value. The cmdlet returns an array of forest restore points (points in time); this example saves the first one to the $restorePoint variable. 3. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domains variable. The cmdlet returns all domains in the forest. 4. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $credentials variable. 6. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $resourcePool variable. 7. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $datastore variable. 8. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $folder variable. 9. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set the root domain (the first element of the $domains array) as the Domain parameter value. Save the first restore point to the $rootRestorePoint variable. 10. Run the [New-VBRViADForestDomainRestoreSpec](new-vbrviadforestdomainrestorespec.md) cmdlet to create the specification for the root domain controller. Specify the following parameters:  * Set the $rootRestorePoint variable as the RestorePoint parameter value. * Set the $credentials variable as the Credentials parameter value. * Set the $server variable as the Server parameter value. * Set the $resourcePool variable as the ResourcePool parameter value. * Set the $datastore variable as the Datastore parameter value. * Set the $folder variable as the Folder parameter value. * Specify the VMName parameter value.   Save the result to the $rootSpec variable.   1. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set a child domain (the second element of the $domains array) as the Domain parameter value. Save the first restore point to the $childRestorePoint variable. 2. Run the [New-VBRViADForestDomainRestoreSpec](new-vbrviadforestdomainrestorespec.md) cmdlet to create the specification for the child domain controller. Specify the same parameters as for the root domain controller, but set the $childRestorePoint variable as the RestorePoint parameter value and specify a different VMName parameter value. Save the result to the $childSpec variable. 3. Run the Start-VBRADForestRestore cmdlet. Specify the following parameters:  * Set the $restorePoint variable as the RestorePoint parameter value. * Set the @($rootSpec, $childSpec) array as the DomainRestoreSpec parameter value. The array must contain exactly one specification for the root domain. * Provide the RunAsync parameter. * Specify the Reason parameter.   Save the result to the $restore variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Microsoft Active Directory Forest Restore to Microsoft Hyper-V

|  |  |
| --- | --- |
| This example shows how to start a Microsoft Active Directory forest restore for a Microsoft Hyper-V environment. It restores two domain controllers — one from the root domain and one from a child domain.  |  | | --- | | $forest = Get-VBRADForest  $restorePoint = (Get-VBRADForestRestorePoint -ADForest $forest)[0]  $domains = Get-VBRADForestDomain -ADForest $forest  $server = Get-VBRServer -Name "hvhost01.company.local"  $credentials = Get-Credential  $rootRestorePoint = (Get-VBRADForestDomainRestorePoint -Domain $domains[0])[0]  $rootSpec = New-VBRHvADForestDomainRestoreSpec -RestorePoint $rootRestorePoint -Credentials $credentials -Server $server -Path "C:\VMs\Restore" -VMName "DC01-Restored"  $childRestorePoint = (Get-VBRADForestDomainRestorePoint -Domain $domains[1])[0]  $childSpec = New-VBRHvADForestDomainRestoreSpec -RestorePoint $childRestorePoint -Credentials $credentials -Server $server -Path "C:\VMs\Restore" -VMName "DC02-Restored"  $reIpRule = New-VBRADForestReIpRule -SourceIp 172.16.\*.\* -SourceMask 255.255.0.0 -TargetIp 172.17.\*.\* -TargetMask 255.255.0.0 -TargetGateway 172.17.0.1 -VlanTag 120  $restore = Start-VBRADForestRestore -RestorePoint $restorePoint -DomainRestoreSpec @($rootSpec, $childSpec) -ReIpRule $reIpRule -RunAsync -Reason "Disaster recovery" |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md) cmdlet. Set the $forest variable as the ADForest parameter value. The cmdlet returns an array of forest restore points (points in time); this example saves the first one to the $restorePoint variable. 3. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domains variable. The cmdlet returns all domains in the forest. 4. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $credentials variable. 6. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set the root domain (the first element of the $domains array) as the Domain parameter value. Save the first restore point to the $rootRestorePoint variable. 7. Run the [New-VBRHvADForestDomainRestoreSpec](new-vbrhvadforestdomainrestorespec.md) cmdlet to create the specification for the root domain controller. Specify the following parameters:  * Set the $rootRestorePoint variable as the RestorePoint parameter value. * Set the $credentials variable as the Credentials parameter value. * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the VMName parameter value.   Save the result to the $rootSpec variable.   1. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set a child domain (the second element of the $domains array) as the Domain parameter value. Save the first restore point to the $childRestorePoint variable. 2. Run the [New-VBRHvADForestDomainRestoreSpec](new-vbrhvadforestdomainrestorespec.md) cmdlet to create the specification for the child domain controller. Specify the same parameters as for the root domain controller, but set the $childRestorePoint variable as the RestorePoint parameter value and specify a different VMName parameter value. Save the result to the $childSpec variable. 3. Run the [New-VBRADForestReIpRule](new-vbradforestreiprule.md) cmdlet to create a re-IP rule. Specify the SourceIp, SourceMask, TargetIp, TargetMask, TargetGateway, and VlanTag parameter values. Save the result to the $reIpRule variable. 4. Run the Start-VBRADForestRestore cmdlet. Specify the following parameters:  * Set the $restorePoint variable as the RestorePoint parameter value. * Set the @($rootSpec, $childSpec) array as the DomainRestoreSpec parameter value. The array must contain exactly one specification for the root domain. * Set the $reIpRule variable as the ReIpRule parameter value. * Provide the RunAsync parameter. * Specify the Reason parameter.   Save the result to the $restore variable to use it with other cmdlets. |

Related Commands

* [Get-VBRADForest](get-vbradforest.md)
* [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md)
* [Get-VBRADForestDomain](get-vbradforestdomain.md)
* [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [New-VBRViADForestDomainRestoreSpec](new-vbrviadforestdomainrestorespec.md)
* [New-VBRHvADForestDomainRestoreSpec](new-vbrhvadforestdomainrestorespec.md)
* [New-VBRADForestReIpRule](new-vbradforestreiprule.md)

Page updated 2026-07-28


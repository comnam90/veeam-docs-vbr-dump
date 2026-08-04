---
title: "New-VBRHvADForestDomainRestoreSpec"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvadforestdomainrestorespec.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRHvADForestDomainRestoreSpec


Short Description

Creates a Hyper-V domain restore specification for a Microsoft Active Directory forest restore.

Applies to

Platform: Hyper-V

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvADForestDomainRestoreSpec [-RestorePoint] <VBRADForestDomainRestorePoint> -Credentials <PSCredential> -Server <CHost> -Path <String> -VMName <String> [-NetworkMapping <VBRHvInstantRecoveryNetworkMappingRule[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRADForestDomainRestoreSpec](vbradforestdomainrestorespec.md) object. This object defines the target settings for restoring a domain controller VM on a Hyper-V host during a Microsoft Active Directory forest restore. Create one specification for each domain controller you want to restore. Use this object with the [Start-VBRADForestRestore](start-vbradforestrestore.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies the domain controller restore point to use for the restore operation. | Accepts the [VBRADForestDomainRestorePoint](vbradforestdomainrestorepoint.md) object. To get this object, run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Credentials | Specifies the guest OS credentials of the restored domain controller. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. | True | Named | False |
| Server | Specifies the Hyper-V host on which to restore the domain controller VM. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the folder on the Hyper-V host where the domain controller VM files will be stored during the restore. | String | True | Named | False |
| VMName | Specifies the name for the restored domain controller VM. | String | True | Named | False |
| NetworkMapping | Specifies an array of network mapping rules for the restore. Use this parameter to map source networks to networks available on the target Hyper-V host. Network mapping is required when you restore the domain controller VM to a host other than the original one. | Accepts the [VBRHvInstantRecoveryNetworkMappingRule](vbrhvinstantrecoverynetworkmappingrule.md)[] object. To get this object, run the [New-VBRHvInstantRecoveryNetworkMappingRule](new-vbrhvinstantrecoverynetworkmappingrule.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestDomainRestoreSpec](vbradforestdomainrestorespec.md) object that defines the target settings for restoring a domain controller VM on a Hyper-V host.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Hyper-V Domain Restore Specification

|  |  |
| --- | --- |
| This example shows how to create a domain restore specification for a Hyper-V environment.  |  | | --- | | $forest = Get-VBRADForest  $domain = Get-VBRADForestDomain -ADForest $forest  $domainRestorePoint = Get-VBRADForestDomainRestorePoint -Domain $domain  $server = Get-VBRServer -Name "hvhost01.company.local"  $credentials = Get-Credential  $hvSpec = New-VBRHvADForestDomainRestoreSpec -RestorePoint $domainRestorePoint[0] -Credentials $credentials -Server $server -Path "C:\VMs\Restore" -VMName "DC01-Restored" |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domain variable. 3. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $domainRestorePoint variable. The cmdlet returns an array of restore points (points in time); this example uses the first one ($domainRestorePoint[0]). 4. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $credentials variable. 6. Run the New-VBRHvADForestDomainRestoreSpec cmdlet. Specify the following parameters:  * Set the $domainRestorePoint[0] variable as the RestorePoint parameter value. * Set the $credentials variable as the Credentials parameter value. * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the VMName parameter value.   Save the result to the $hvSpec variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Hyper-V Domain Restore Specification with Network Mapping

|  |  |
| --- | --- |
| This example shows how to create a domain restore specification with network mapping for a Hyper-V environment.  |  | | --- | | $forest = Get-VBRADForest  $domain = Get-VBRADForestDomain -ADForest $forest  $domainRestorePoint = Get-VBRADForestDomainRestorePoint -Domain $domain  $server = Get-VBRServer -Name "hvhost01.company.local"  $credentials = Get-Credential  $sourceNetwork = Get-VBRComputerNetworkInfo  $targetNetwork = Get-VBRHvServerNetworkInfo -Server $server  $networkMapping = New-VBRHvInstantRecoveryNetworkMappingRule -SourceNetwork $sourceNetwork -TargetNetwork $targetNetwork  $hvSpec = New-VBRHvADForestDomainRestoreSpec -RestorePoint $domainRestorePoint[0] -Credentials $credentials -Server $server -Path "C:\VMs\Restore" -VMName "DC01-Restored" -NetworkMapping $networkMapping |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domain variable. 3. Run the [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $domainRestorePoint variable. The cmdlet returns an array of restore points (points in time); this example uses the first one ($domainRestorePoint[0]). 4. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 5. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $credentials variable. 6. Run the [Get-VBRComputerNetworkInfo](get-vbrcomputernetworkinfo.md) cmdlet. Save the result to the $sourceNetwork variable. 7. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $targetNetwork variable. 8. Run the [New-VBRHvInstantRecoveryNetworkMappingRule](new-vbrhvinstantrecoverynetworkmappingrule.md) cmdlet. Set the $sourceNetwork variable as the SourceNetwork parameter value. Set the $targetNetwork variable as the TargetNetwork parameter value. Save the result to the $networkMapping variable. 9. Run the New-VBRHvADForestDomainRestoreSpec cmdlet. Specify the following parameters:  * Set the $domainRestorePoint[0] variable as the RestorePoint parameter value. * Set the $credentials variable as the Credentials parameter value. * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the VMName parameter value. * Set the $networkMapping variable as the NetworkMapping parameter value.   Save the result to the $hvSpec variable to use it with other cmdlets. |

Related Commands

* [Get-VBRADForest](get-vbradforest.md)
* [Get-VBRADForestDomain](get-vbradforestdomain.md)
* [Get-VBRADForestDomainRestorePoint](get-vbradforestdomainrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRComputerNetworkInfo](get-vbrcomputernetworkinfo.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [New-VBRHvInstantRecoveryNetworkMappingRule](new-vbrhvinstantrecoverynetworkmappingrule.md)
* [Start-VBRADForestRestore](start-vbradforestrestore.md)

Page updated 2026-07-28


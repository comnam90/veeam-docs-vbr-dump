---
title: "Set-VBRUniversalCDPPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbruniversalcdppolicy.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Set-VBRUniversalCDPPolicy


Short Description

Modifies a universal CDP policy.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRUniversalCDPPolicy -Policy <VBRUniversalCDPPolicy> [-SourceObject <VBRUniversalCDPSource[]>] [-ExcludedObject <VBRUniversalCDPSource[]>] [-Destination <IUniversalCdpDestination>] [-Name <string>] [-Description <string>] [-EnableNetworkMapping] [-NetworkMapping <VBRUniversalCDPNetworkMappingRule[]>] [-SourceProxy <VBRCDPProxy[]>] [-TargetProxy <VBRCDPProxy[]>] [-Suffix <string>] [-CompressionLevel {None | DedupeFriendly | Optimal | High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a universal CDP policy.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies the universal CDP policy whose settings you want to change. | Accepts the VBRUniversalCDPPolicy object. To create this object, run the [Add-VBRUniversalCDPPolicy](add-vbruniversalcdppolicy.md) cmdlet. To get this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True |
| SourceObject | Specifies the workloads or protection groups that you want to protect with universal CDP. | Accepts the VBRUniversalCDPSource[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) or [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | False | Named | False |
| ExcludedObject | Specifies the array of workloads that you want to exclude from the universal CDP policy processing. | Accepts the VBRUniversalCDPSource[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False | Named | False |
| Destination | Specifies the settings of the target location where the workloads will be replicated. | Accepts the IUniversalCdpDestination object. To get this object, run the [New-VBRUniversalCDPViDestination](new-vbruniversalcdpvidestination.md) cmdlet. | False | Named | False |
| Name | Specifies a name for the universal CDP policy. | String | False | Named | False |
| Description | Specifies a description for the universal CDP policy. | String | False | Named | False |
| EnableNetworkMapping | Defines if network mapping is enabled for the universal CDP policy. | SwitchParameter | False | Named | False |
| NetworkMapping | Specifies the array of network mapping settings. | Accepts the VBRUniversalCDPNetworkMappingRule[] object. To get this object, run the [New-VBRUniversalCDPNetworkMappingRule](new-vbruniversalcdpnetworkmappingrule.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the array of the source CDP proxies that you want to use. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies the array of the target CDP proxies that you want to use. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that the cmdlet will add to the name of replicas. | String | False | Named | False |
| CompressionLevel | Specifies the compression level of the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level. | [VBRCompressionLevel](enums.md#VBRCompressionLevel) | False | Named | False |
| NotificationOptions | Specifies notification settings of the universal CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionOptions | Specifies retention settings of the universal CDP policy. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUniversalCDPPolicy object that defines settings of the universal CDP policy.

Examples

This example shows how to exclude a workload from the universal CDP policy processing.

|  |
| --- |
| $cdpPolicy = Get-VBRCDPPolicy -Name "Universal CDP Policy"  $group = Get-VBRProtectionGroup -Name "Protection Group CDP"  $workloads = Get-VBRDiscoveredComputer -ProtectionGroup $group  Set-VBRUniversalCDPPolicy -Policy $cdpPolicy -ExcludedObject $workloads[0] |

Perform the following steps:

1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $cdpPolicy variable.
2. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
3. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $workloads variable.
4. Run the Set-VBRUniversalCDPPolicy cmdlet. Set the $cdpPolicy variable as the Policy parameter value. Set the $workloads[0] variable as the ExcludedObject parameter value.

Related Commands

* [Get-VBRCDPPolicy](get-vbrcdppolicy.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)



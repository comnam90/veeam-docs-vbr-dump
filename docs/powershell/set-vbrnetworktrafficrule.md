---
title: "Set-VBRNetworkTrafficRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnetworktrafficrule.html"
last_updated: "9/8/2025"
product_version: "13.0.1.1071"
---

# Set-VBRNetworkTrafficRule


Short Description

Modifies network traffic rules.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNetworkTrafficRule -Rule <VBRNetworkTrafficRule> [-Name <string>] [-SourceIPStart <ipaddress>] [-SourceIPEnd <ipaddress>] [-TargetIPStart <ipaddress>] [-TargetIPEnd <ipaddress>] [-EnableEncryption] [-EnableThrottling] [-AllowRestoreThrottling] [-ThrottlingUnit <VBRSpeedUnit> {MbitPerSec | MbytePerSec | KbytePerSec}] [-ThrottlingValue <int>] [-EnableThrottlingWindow] [-ThrottlingWindowOptions <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies network traffic rules.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Rule | Specifies a network traffic rule that you want to modify. | Accepts the VBRNetworkTrafficRule object. To get this object, run the [Get-VBRNetworkTrafficRule](get-vbrnetworktrafficrule.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a that you want to assign to a network traffic rule. | String | False | Named | False |
| SourceIPStart | Specifies the first IP address of the IP source range. | IPAddress | False | Named | False |
| SourceIPEnd | Specifies the last IP address of the IP source range. | IPAddress | False | Named | False |
| TargetIPStart | Specifies the first IP address of the IP target range. | IPAddress | False | Named | False |
| TargetIPEnd | Specifies the last IP address of the IP target range. | IPAddress | False | Named | False |
| EnableEncryption | Enables encryption for a network traffic rule. Veeam Backup & Replication will encrypt the data that is passed between backup infrastructure components on the source and target side. | SwitchParameter | False | Named | False |
| EnableThrottling | Enables throttling for a network traffic rule. Veeam Backup & Replication will limit the traffic throughput between the backup infrastructure components within the specified IP range.  Use the following parameters to set the maximum value:   * ThrottlingValue * ThrottlingUnit | SwitchParameter | False | Named | False |
| ThrottlingValue | Specifies the maximum speed value that must be used to transfer VM machine data from source to target. | Int32 | False | Named | False |
| ThrottlingUnit | For the EnableThrottling parameter.  Specifies the measuring unit for the ThrottlingValue parameter: You can set the following units:   * MbitPerSec * MbytePerSec * KbytePerSec   Default: MbitPerSec. | VBRSpeedUnit | False | Named | False |
| EnableThrottlingWindow | Enables the schedule for a network traffic rule. | SwitchParameter | False | Named | False |
| ThrottlingWindowOptions | Specifies the time intervals during which Veeam Backup & Replication must apply a network traffic rule. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| AllowRestoreThrottling | Enables throttling for restore operations. Veeam Backup & Replication will limit restore operation traffic between backup infrastructure components within the specified IP range. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNetworkTrafficRule](vbrnetworktrafficrule.md)

Examples

Enabling Encyption for Network Traffic Rule

This example shows how to enable encryption for a network traffic rule.

|  |
| --- |
| $rule = Get-VBRNetworkTrafficRule -Name "New rule"  Set-VBRNetworkTrafficRule -Rule $rule -EnableEncryption |

Perform the following steps:

1. Run the [Get-VBRNetworkTrafficRule](get-vbrnetworktrafficrule.md) cmdlet. Specify the Name parameter value. Save the result to the $rule variable.
2. Run the Set-VBRNetworkTrafficRule cmdlet. Set the $rule variable as the Rule parameter value. Provide the EnableEncryption parameter.

Related Commands

[Get-VBRNetworkTrafficRule](get-vbrnetworktrafficrule.md)



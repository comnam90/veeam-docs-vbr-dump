---
title: "Set-VBRReplicaApplicationProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrreplicaapplicationprocessingoptions.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRReplicaApplicationProcessingOptions


Short Description

Modifies guest processing settings for Cloud Director replica jobs and CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRReplicaApplicationProcessingOptions -ReplicaApplicationProcessingOptions <VBRReplicaApplicationProcessingOptions> [-GuestInteractionProxy <CHost[]>] [-GuestOSCredentials <CCredentials>] [-ApplicationProcessingOptions <VBRApplicationProcessingOptions[]>] [-IndividualGuestOSCredentials <VBRIndividualGuestOSCredentials[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies guest processing settings for Cloud Director replica jobs and CDP policies.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ReplicaApplicationProcessingOptions | Specifies guest processing settings that you want to modify. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | True | Named | False |
| GuestInteractionProxy | Specifies an arraof of VMs that will be used as guest interaction proxies. | Accepts the CHost[] object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| GuestOSCredentials | Specifies a user account that will be used to connect to VMs added to the Cloud Director replica jobs or CDP policies and deploy the runtime process on their guest OSes. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| ApplicationProcessingOptions | Specifies application-aware processing settings. | Accepts the VBRApplicationProcessingOptions[] object. To create this object, run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| IndividualGuestOSCredentials | Specifies a user account that will be used connect to the specific VMs guest OSes. | Accepts the VBRIndividualGuestOSCredentials[] object. To create this object, run the [New-VBRIndividualGuestOSCredentials](new-vbrindividualguestoscredentials.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRReplicaApplicationProcessingOptions object that defines guest processing settings for CDP policies.

Examples

Modifying Guest Processing Settings for CDP Policies

This example shows how to assign the CDP Admin user account to the WinSrv2073 VM guest OS.

|  |
| --- |
| $vm = Find-VBRViEntity -Name "WinSrv2073"  $credentials = Get-VBRCredentials -Name "CDP Admin"  $oscreds = New-VBRIndividualGuestOSCredentials -IndividualMachine $vm -MachineCredentials $credentials  Set-VBRReplicaApplicationProcessingOptions -IndividualGuestOSCredentials $oscreds |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable.
3. Run the [New-VBRIndividualGuestOSCredentials](new-vbrindividualguestoscredentials.md) cmdlet. Specify the IndividualMachine and MachineCredentials  parameters. Save the result to the $oscreds variable.
4. Run the Set-VBRReplicaApplicationProcessingOptions cmdlet. Set the $oscreds variable as the IndividualGuestOSCredentials parameter value.

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRIndividualGuestOSCredentials](new-vbrindividualguestoscredentials.md)



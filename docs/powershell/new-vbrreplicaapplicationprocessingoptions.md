---
title: "New-VBRReplicaApplicationProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrreplicaapplicationprocessingoptions.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRReplicaApplicationProcessingOptions

In this article

Short Description

Defines guest processing settings for Cloud Director replica jobs and CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRReplicaApplicationProcessingOptions [-GuestInteractionProxy <CHost[]>] [-GuestOSCredentials <CCredentials>] [-ApplicationProcessingOptions <VBRApplicationProcessingOptions[]>] [-IndividualGuestOSCredentials <VBRIndividualGuestOSCredentials[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRReplicaApplicationProcessingOptions object. This object defines guest processing settings for Cloud Director replica jobs and CDP policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| GuestInteractionProxy | Specifies an array of VMs that will be used as guest interaction proxies. | Accepts the CHost[] object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| GuestOSCredentials | Specifies a user account that will be used to connect to VMs added to the job and deploy a runtime process on their guest OSes. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| ApplicationProcessingOptions | Specifies an array of application-aware processing settings. | Accepts the VBRApplicationProcessingOptions[] object. To create this object, run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| IndividualGuestOSCredentials | Specifies a user account that will used to connect to the specific machine guest OS. | Accepts the VBRIndividualGuestOSCredentials[] object. To create this object, run the [New-VBRIndividualGuestOSCredentials](new-vbrindividualguestoscredentials.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRReplicaApplicationProcessingOptions object that defines guest processing settings for a CDP policy.

Examples

Defining Guest Interaction Proxy for CDP Policy Guest Processing Settings

This example shows how to define the WinG2073 machine as a guest interaction proxy for guest processing settings of a CDP policy.

|  |
| --- |
| $proxy = Get-VBRServer -Name "WinG2073"  New-VBRReplicaApplicationProcessingOptions -GuestInteractionProxy $proxy |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
2. Run the New-VBRReplicaApplicationProcessingOptions cmdlet. Set the $proxy variable as the GuestInteractionProxy parameter value.

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071

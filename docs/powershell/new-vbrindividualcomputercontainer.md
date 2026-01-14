---
title: "New-VBRIndividualComputerContainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrindividualcomputercontainer.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# New-VBRIndividualComputerContainer

In this article

Short Description

Creates a scope of computers for a protection group.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRIndividualComputerContainer -CustomCredentials <VBRIndividualComputerCustomCredentials[]>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRIndividualComputerContainer](vbrindividualcomputercontainer.md) object. This object contains a scope of computers. Use this object to create a protection group with the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| CustomCredentials | Specifies computers and a method for authenticating them. | Accepts the [VBRIndividualComputerCustomCredentials[]](vbrindividualcomputercustomcredentials.md) object. To get this object, run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. | True | Named | True (ByValue ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRIndividualComputerContainer](vbrindividualcomputercontainer.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Scope of Computers for Protection Group

|  |  |
| --- | --- |
| This example shows how to create a scope of computers for a protection group.  |  | | --- | | $computers = @("172.19.51.53", "sup-v8931") | ForEach { New-VBRIndividualComputerCustomCredentials -HostName $\_ -Credentials "support\jsmith" }  New-VBRIndividualComputerContainer -CustomCredentials $computers |  Perform the following steps:   1. Run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. Use the ForEach statement to apply the same credentials to multiple computers. Save the result to the $computers variable. 2. Run the New-VBRIndividualComputerContainer cmdlet. Set the $computers variable as the CustomCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Protection Group with Scope of Computers

|  |  |
| --- | --- |
| This example shows how to create a protection group with a scope of computers.  |  | | --- | | $computers = @("172.19.51.53", "sup-v8931") | ForEach { New-VBRIndividualComputerCustomCredentials -HostName $\_ -Credentials "support\jsmith" }  $compscope = New-VBRIndividualComputerContainer -CustomCredentials $computers  Add-VBRProtectionGroup -Name "Computers" -Container $compscope |  Perform the following steps:   1. Create a scope of computers:  * Run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. Use the ForEach statement to apply the same credentials to multiple computers. Save the result to the $computers variable. * Run the New-VBRIndividualComputerContainer cmdlet. Set the $computers variable as the CustomCredentials parameter value. Save the result to the $compscope variable.  1. Create a protection group. To do this, run the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Set the $compscope variable as the Container parameter value. |

Related Commands

* [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md)
* [Add-VBRProtectionGroup](add-vbrprotectiongroup.md)

Page updated 2/11/2025

Page content applies to build 13.0.1.1071

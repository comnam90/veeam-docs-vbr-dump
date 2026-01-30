---
title: "Set-VBRIndividualComputerContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrindividualcomputercontainer.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# Set-VBRIndividualComputerContainer


Short Description

Modifies a scope of individual computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRIndividualComputerContainer -Container <VBRIndividualComputerContainer> [-CustomCredentials <VBRIndividualComputerCustomCredentials[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRIndividualComputerContainer](vbrindividualcomputercontainer.md) object. This object contains the scope of computers you want to add to a protection group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies the scope of computers you want to add to a protection group. | Accepts the [VBRIndividualComputerContainer](vbrindividualcomputercontainer.md) object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet and use the Container property. | True | Named | True (ByValue ByProperty Name) |
| CustomCredentials | Specifies individual computers and a method for authenticating them. | Accepts the [VBRIndividualComputerCustomCredentials[]](vbrindividualcomputercustomcredentials.md) object. To get this object, run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRIndividualComputerContainer](vbrindividualcomputercontainer.md)

Examples

Adding Computer to Protection Group

This example shows how to add a computer to the Computers protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name Computers  $comp = $group.Container.CustomCredentials  $supervisor = New-VBRIndividualComputerCustomCredentials -HostName support.east.local -Credentials support\jsmith  $comp += $supervisor  $newcomp = Set-VBRIndividualComputerContainer -Container $group.Container -CustomCredentials $comp  Set-VBRProtectionGroup -ProtectionGroup $group -Container $newcomp |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Get individual computers. Use the Container.CustomCredentials property of the $group variable. Save the result to the $comp variable.
3. Run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. Specify the HostName and the Credentials parameter values. Save the result to the $supervisor variable.
4. Add the computer to the group of computers in the $comp variable. Use the += operator.
5. Run the Set-VBRIndividualComputerContainer cmdlet. Set the Container property of the $group variable as the Container parameter value. Set the $comp variable as the CustomCredentials parameter value. Save the result to the $newcomp variable.
6. Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $newcomp variable as the Container parameter value.

Related Commands

* [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Set-VBRProtectionGroup](set-vbrprotectiongroup.md)



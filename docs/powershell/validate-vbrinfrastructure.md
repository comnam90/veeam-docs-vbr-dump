---
title: "Validate-VBRInfrastructure"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/validate-vbrinfrastructure.html"
last_updated: "4/23/2024"
product_version: "13.0.1.1071"
---

# Validate-VBRInfrastructure


Short Description

Validates the network infrastructure of a backup server.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Validate-VBRInfrastructure [-EnableIPv6]  [<CommonParameters>] |

Detailed Description

This cmdlet validates the network infrastructure of a backup server and verifies whether IPv6 is allowed to use in the network infrastructure. After the verification completes, the cmdlet returns the error report with the Reports and Success properties. Depending on the result, the Success property contains the following values:

* True — If the Reports array is empty.
* False — If the Reports array contains details with errors.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableIPv6 | Defines that the IPv6 is allowed in the network infrastructure. | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRInfrastructureValidationResult](vbrinfrastructurevalidationresult.md)

Examples

Validating Network Infrastructure of Backup Server

This command validates the network infrastructure of a backup server.

|  |
| --- |
| Validate-VBRInfrastructure -EnableIPv6 |



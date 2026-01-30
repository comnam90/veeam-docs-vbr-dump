---
title: "Add-VBRCloudGatewayCertificate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudgatewaycertificate.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudGatewayCertificate


Short Description

Assigns a TLS certificate to the service provider.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Assign a certificate from the certificate store.

|  |
| --- |
| Add-VBRCloudGatewayCertificate -Certificate <VBRCloudCertificate> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Assign a certificate using the PFX and KEY files associated with the certificate.

|  |
| --- |
| Add-VBRCloudGatewayCertificate -CertificatePath <String> -PrivateKeyPath <String> [-Password <SecureString>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet assigns a TLS certificate to the service provider.

|  |
| --- |
| Important |
| You can only use the TLS certificate imported from the certificate store. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Certificate | Specifies the certificate you want to use. | Accepts the [VBRCloudCertificate](vbrcloudcertificate.md) object. To get this object, run the [Get-VBRCloudGatewayCertificate](get-vbrcloudgatewaycertificate.md) cmdlet. | True | Named | True (ByValue, |
| CertificatePath | Specifies the full path to the PFX file associated with the certificate. | String | True | Named | False |
| Password | Specifies the full path to the KEY file associated with the certificate. | SecureString | False | Named | False |
| PrivateKeyPath | Specifies a secure string that contains the password for the certificate file, if the file is protected. | String | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assigning Certificate using Certificate Files

|  |  |
| --- | --- |
| This example shows how to assign a certificate using certificate files.  |  | | --- | | Add-VBRCloudGatewayCertificate -CertificatePath "C:\Certs\TechCompany.pfx" -PrivateKeyPath  "C:\Certs\OmegaCompany.key" -Password (Read-Host -AsSecureString "Enter certificate password") | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Assigning TLS Certificate to Service Provider

|  |  |
| --- | --- |
| This example shows how to get a certificate from the certificate store and assign it to the service provider.  |  | | --- | | $certificate = Get-VBRCloudGatewayCertificate -FromStore | Where FriendlyName -eq "Omega Company"  Add-VBRCloudGatewayCertificate -Certificate $certificate |  Perform the following steps:   1. Run the [Get-VBRCloudGatewayCertificate](get-vbrcloudgatewaycertificate.md) cmdlet. Provide the FromStore parameter value. Pipe the cmdlet output to the Where command to filter certificates by the FriendlyName parameter. Save the result to the $certificate variable. 2. Run the Add-VBRCloudGatewayCertificate cmdlet. Set the $certificate variable as the Certificate parameter value. |

Related Commands

[Get-VBRCloudGatewayCertificate](get-vbrcloudgatewaycertificate.md)



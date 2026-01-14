---
title: "Add-VBRBackupServerCertificate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrbackupservercertificate_agent.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# Add-VBRBackupServerCertificate

In this article

Short Description

Specifies a TLS certificate used to establish secure communication from backup infrastructure components to the backup server.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Assign a certificate from the certificate store.

|  |
| --- |
| Add-VBRBackupServerCertificate -Certificate <VBRBackupServerCertificate> [-WhatIf] [-Confirm] [<CommonParameters>] |

* Assign a certificate using the .CRT or .PEM and .KEY files associated with the certificate.

|  |
| --- |
| Add-VBRBackupServerCertificate -CertificatePath <String> -PrivateKeyPath <String> [-Password <SecureString>]  [-WhatIf] [-Confirm] [<CommonParameters>] |

Detailed Description

This cmdlet specifies a TLS certificate to be used to establish a secure connection from backup infrastructure components to the backup server. You can generate a new self-signed TLS certificate or import an existing TLS certificate from the Microsoft Windows certificate store.

|  |
| --- |
| Important |
| Consider the following:   * With Veeam PowerShell, you cannot import a TLS certificate from a file in the PFX format. * Changing the TLS certificate requires the restart of the backup service. All active backup and restore tasks will be interrupted. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Certificate | Specifies the certificate you want to use. | Accepts the VBRBackupServerCertificate object. To create this object, run the [Get-VBRBackupServerCertificate](get-vbrbackupservercertificate.md) cmdlet. | True | Named | True (ByValue, |
| CertificatePath | Specifies the full path to the .CRT or .PEM file associated with the certificate. | String | True | Named | False |
| Password | Specifies the full path to the KEY file associated with the certificate. | SecureString | False | Named | False |
| PrivateKeyPath | Specifies a secure string that contains the password for the certificate file. | String | True | Named | False |
| Name | Note: This parameter is obsolete.  Specifies a friendly name for the self-signed TLS certificate. | String | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupServerCertificate object that contains TLS certificates.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assigning Certificate using Certificate Files

|  |  |
| --- | --- |
| This example shows how to assign a certificate using certificate files.  |  | | --- | | Add-VBRBackupServerCertificate -CertificatePath "C:\Certs\TechCompany.crt" -PrivateKeyPath  "C:\Certs\OmegaCompany.key" -Password (Read-Host -AsSecureString "Enter certificate password") | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Importing Certificate from Certificate Store

|  |  |
| --- | --- |
| This example shows how to import an existing TLS certificate signed by a CA from the Microsoft Windows certificate store.  |  | | --- | | $certificate = Get-VBRBackupServerCertificate -FromStore | Where FriendlyName -eq "ABC"  Add-VBRBackupServerCertificate -Certificate $certificate |  Perform the following steps:   1. Run the [Get-VBRBackupServerCertificate](get-vbrbackupservercertificate.md) cmdlet. Provide the FromStore parameter value. Pipe the cmdlet output to the Where command to find certificates with ABC in the FriendlyName property. Save the result to the $certificate variable. 2. Run the Add-VBRBackupServerCertificate cmdlet. Set the $certificate variable as the Certificate parameter value. |

Related Commands

[Get-VBRBackupServerCertificate](get-vbrbackupservercertificate.md)

Page updated 9/3/2024

Page content applies to build 13.0.1.1071

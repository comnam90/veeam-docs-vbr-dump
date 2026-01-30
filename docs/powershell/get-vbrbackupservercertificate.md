---
title: "Get-VBRBackupServerCertificate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackupservercertificate.html"
last_updated: "1/5/2026"
product_version: "13.0.1.1071"
---

# Get-VBRBackupServerCertificate


Short Description

Returns TLS certificates.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get the TLS certificate from the Microsoft Windows Certificate store.

|  |
| --- |
| Add-VBRBackupServerCertificate -Certificate <VBRBackupServerCertificate>  [-WhatIf] [-Confirm] [<CommonParameters>] |

* Get the TLS current certificate.

|  |
| --- |
| Add-VBRBackupServerCertificate -Name <String>  [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Get the TLS certificate from a PFX file.

|  |
| --- |
| Get-VBRBackupServerCertificate -Path <String> [-Password <SecureString>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the TLS certificates.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FromStore | Defines that the cmdlet will return the TLS certificate present in the local certificate store on this server. If you run the cmdlet without this parameter, it will return the certificate that is currently used. | SwitchParameter | True | Named | False |
| Path | Specifies a path to the PXF file. The cmdlet will return TLS certificate that are available at this path. | String | True | Named | False |
| Password | Specifies a password for a PXF file. | SecureString | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupServerCertificate object that contains TLS certificates.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Currently Imported TLS Certificates

|  |  |
| --- | --- |
| This command returns the TLS  certificate that is currently imported to the backup server.  |  | | --- | | Get-VBRBackupServerCertificate | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting TLS Certificates from Microsoft Windows Certificate Store

|  |  |
| --- | --- |
| This command gets a TLS certificate from the Microsoft Windows Certificate store.  |  | | --- | | Get-VBRBackupServerCertificate -FromStore | Where FriendlyName -eq "ABC" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Certificates from PFX Files

|  |  |
| --- | --- |
| This command gets a TLS certificate from a PFX file.  |  | | --- | | Get-VBRBackupServerCertificate -Path "C:\cert\AMB\_cert.pfx" | |



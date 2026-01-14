---
title: "Generate-VBRBackupServerCertificate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/generate-vbrbackupservercertificate.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Generate-VBRBackupServerCertificate

In this article

Short Description

Generates a TLS certificate that is used to establish a secure connection from backup infrastructure components to the backup server.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Generate-VBRBackupServerCertificate -Name <String>  [-WhatIf] [-Confirm] [<CommonParameters>] |

Detailed Description

This cmdlet generates a TLS certificate that is used to establish a secure connection from backup infrastructure components to the backup server. The cmdlet will save the certificate to the local computer certificate store.

To assign the certificate to the cloud gateways, run the [Add-VBRCloudGatewayCertificate](add-vbrcloudgatewaycertificate.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a friendly name for the self-signed TLS certificate. | String | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupServerCertificate object that defines the settings of a TLS certificate used to connect to the backup server.

Examples

Generating TLS Certificate

This command generates a TLS certificate in Veeam Backup & Replication.

|  |
| --- |
| Add-VBRBackupServerCertificate -Name "veeam-bk01.tech.local" |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071

---
title: "Import-VBRLinuxKnownHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrlinuxknownhost_agent.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# Import-VBRLinuxKnownHost

In this article

Short Description

Imports Linux TLS fingerprints from a file.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Import-VBRLinuxKnownHost -Path <string> [-NetworkCredentials <CCredentials>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet imports TLS fingerprints of Linux hosts from a file to Veeam Backup & Replication. Veeam Backup & Replication will consider the hosts as trusted.

|  |
| --- |
| Tip |
| To instruct Veeam Backup & Replication to establish connections only with trusted hosts, run the [Set-VBRLinuxTrustedHostPolicy](set-vbrlinuxtrustedhostpolicy.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the path to the file. The cmdlet will import TLS fingerprints from this file. | String | True | Named | True (ByValue, |
| NetworkCredentials | For importing from a folder on a file share.  Specifies the credentials you want to use for authenticating with the shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |
| Force | Defines that the cmdlet will overwrite TLS fingerprints for existing hosts in the Veeam Backup & Replication database without asking a user. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Importing Linux TLS Fingerprints

This command imports Linux TLS fingerprints from an XML file.

|  |
| --- |
| Import-VBRLinuxKnownHost -Path "C:\fingerprints.xml" |

Page updated 9/3/2024

Page content applies to build 13.0.1.1071

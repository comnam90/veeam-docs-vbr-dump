---
title: "Set-VBRLinuxTrustedHostPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrlinuxtrustedhostpolicy.html"
last_updated: "1/17/2025"
product_version: "13.0.1.1071"
---

# Set-VBRLinuxTrustedHostPolicy

In this article

Short Description

Sets the trust policy for Linux hosts.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRLinuxTrustedHostPolicy -Type <VBRLinuxTrustedHostPolicyType> {All | KnownHosts} [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet sets the trust policy for Linux hosts. The policy determines which protected computers running Linux OS are allowed to connect to the backup server. Veeam Backup & Replication recognizes a host as trusted if this host has connected to the Veeam backup server before. Veeam Backup & Replication remembers trusted hosts and keeps them in a database. You can add trusted hosts to the database manually by importing hosts SSH fingerprints from a file.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the trust policy type. You can set the trust policy one of the following types:   * All: Use this option if you want to allow all newly discovered Linux hosts to connect to the backup server. * KnownHosts: Use this option if you want to allow all only trusted Linux hosts to connect to the backup server. | VBRLinuxTrustedHostPolicyType | True | Named | True (ByValue, |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRLinuxTrustedHostPolicy](vbrlinuxtrustedhostpolicy.md)

Examples

Setting up Connections with Trusted Linux Hosts

This command instructs Veeam Backup & Replication to establish connections only with trusted Linux hosts.

|  |
| --- |
| C:\Users\Administrator> Set-VBRLinuxTrustedHostPolicy -Type KnownHosts -PassThru |

Page updated 1/17/2025

Page content applies to build 13.0.1.1071

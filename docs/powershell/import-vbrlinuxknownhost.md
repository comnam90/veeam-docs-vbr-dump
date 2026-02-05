---
title: "Import-VBRLinuxKnownHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrlinuxknownhost.html"
last_updated: "2/4/2026"
product_version: "13.0.1.1071"
---

# Import-VBRLinuxKnownHost


Short Description

Imports trusted Linux SSH and deployer certificate fingerprints from a file.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Import-VBRLinuxKnownHost -Path <string> [-NetworkCredentials <CCredentials>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet imports trusted Linux SSH and deployer certificate fingerprints from the specified file to Veeam Backup & Replication. Veeam Backup & Replication will consider the hosts as trusted.

The file can contain the following fingerprints:

* Microsoft Windows and Linux deployer service certificate fingerprints of servers added as managed to the backup infrastructure.
* Trusted Linux server SSH fingerprints of servers added to the protection groups created for Veeam Agents and servers protected by Veeam Plug-ins for Enterprise Applications.

|  |
| --- |
| Tip |
| To instruct Veeam Backup & Replication to establish connections only with trusted hosts, run the [Set-VBRLinuxTrustedHostPolicy](set-vbrlinuxtrustedhostpolicy.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the path to the file on the backup server. The cmdlet will import TLS fingerprints from this file.  Note: For the Linux-based backup server, the path must start with /var/lib/veeam/. | String | True | Named | True (ByValue, |
| NetworkCredentials | For importing from a folder on a file share. Applies only to Microsoft Windows-based backup servers.  Specifies the credentials you want to use for authenticating with the shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |
| Force | Defines that the cmdlet will overwrite TLS fingerprints for existing hosts in the Veeam Backup & Replication database without asking a user. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Importing Fingerprints

This command imports SSH and deployer certificate fingerprints from an XML file.

|  |
| --- |
| Import-VBRLinuxKnownHost -Path "/var/lib/veeam/export/fingerprints.xml" |



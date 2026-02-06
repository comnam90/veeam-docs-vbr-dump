---
title: "Export-VBRLinuxKnownHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrlinuxknownhost.html"
last_updated: "2/4/2026"
product_version: "13.0.1.1071"
---

# Export-VBRLinuxKnownHost


Short Description

Exports trusted Linux SSH and deployer certificate fingerprints to a file on the backup server.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRLinuxKnownHost -Path <string>  [<CommonParameters>] |

Detailed Description

This cmdlet copies fingerprints from Veeam Backup & Replication to a file on the backup server. The cmdlet copies fingerprints of the following trusted servers:

* For servers added as managed to the backup infrastructure, Veeam Backup & Replication copies Microsoft Windows and Linux deployer service certificate fingerprints.
* For servers added to the protection groups created for Veeam Agents and servers protected by Veeam Plug-ins for Enterprise Applications, Veeam Backup & Replication copies trusted Linux server SSH fingerprints.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the path to the file on the backup server. The cmdlet will export TLS fingerprints to this file.  Note: For the Linux-based backup server, the path must start with /var/lib/veeam/. | String | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Exporting Fingerprints

This command exports SSH and deployer certificate fingerprints to an XML file.

|  |
| --- |
| Export-VBRLinuxKnownHost -Path "/var/lib/veeam/export/fingerprints.xml" |



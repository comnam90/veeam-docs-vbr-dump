---
title: "Export-VBRLinuxKnownHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrlinuxknownhost_agent.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# Export-VBRLinuxKnownHost

In this article

Short Description

Exports Linux SSH fingerprints to a file.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRLinuxKnownHost -Path <string>  [<CommonParameters>] |

Detailed Description

This cmdlet copies TLS fingerprints of trusted Linux hosts from Veeam Backup & Replication to a file.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the path to the file. The cmdlet will export TLS fingerprints to this file. | String | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Exporting Linux SSH Fingerprints

This command exports Linux TLS fingerprints to an XML file.

|  |
| --- |
| Export-VBRLinuxKnownHost -Path "C:\fingerprints.xml" |

Page updated 9/3/2024

Page content applies to build 13.0.1.1071

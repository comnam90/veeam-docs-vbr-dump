---
title: "Veeam Agent Management Security Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/veeam_agent_security_settings.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# Veeam Agent Management Security Settings

In this article

You can use the cmdlets in this topic to perform the following operations.

| Cmdlet | Operation |
| --- | --- |
| [Get-VBRBackupServerCertificate](get-vbrbackupservercertificate_agent.md) | Returns SSL certificates. |
| [Add-VBRBackupServerCertificate](add-vbrbackupservercertificate_agent.md) | Assigns an SSL certificate to the Veeam backup server. |
| [Get-VBRLinuxTrustedHostPolicy](get-vbrlinuxtrustedhostpolicy_agent.md) | Returns the currently set trust policy for Linux hosts. |
| [Set-VBRLinuxTrustedHostPolicy](set-vbrlinuxtrustedhostpolicy_agent.md) | Sets the trust policy for Linux hosts. |
| [Import-VBRLinuxKnownHost](import-vbrlinuxknownhost_agent.md) | Imports Linux SSH fingerprints from a file. |
| [Export-VBRLinuxKnownHost](export-vbrlinuxknownhost_agent.md) | Exports Linux SSH fingerprints to a file. |
| [Reset-VBRProtectionGroupCertificate](reset-vbrprotectiongroupcertificate.md) | Removes a certificate associated with a protection group with a flexible scope. |

|  |
| --- |
| Note |
| With Veeam PowerShell, you cannot create a self-signed certificate or import an SSL certificate from file in the PFX format. You can only select an existing SSL certificate from the Microsoft Windows Certificates store. The certificate must be imported into the certificate store beforehand. |

Page updated 9/3/2024

Page content applies to build 13.0.1.1071

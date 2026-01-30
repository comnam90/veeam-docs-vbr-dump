---
title: "Set-VBRSecurityOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsecurityoptions.html"
last_updated: "4/3/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSecurityOptions


Short Description

Modifies Veeam Backup & Replication security settings.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSecurityOptions [-HostPolicy <VBRLinuxTrustedHostPolicy>] [-AuditLogPath <string>] [-CompressAuditLogs] [-EnableFipsCompliantMode]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the following Veeam Backup & Replication security settings:

* Trust policy for Linux hosts
* Audit logs settings

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HostPolicy | Specifies the trust policy for Linux hosts. | Accepts the VBRLinuxTrustedHostPolicy object. To create this object, run the [Get-VBRLinuxTrustedHostPolicy](get-vbrlinuxtrustedhostpolicy.md) cmdlet. | False | Named | False |
| AuditLogPath | Specifies the path to the folder where Veeam Backup & Replication stores audit logs.  Default: %ProgramData%\Veeam\Backup\Audit. | String | False | Named | False |
| CompressAuditLogs | Defines that the cmdlet will compress the previous versions of audit logs. If you do not provide this parameter, Veeam Backup & Replication will keep all logs without compression.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableFipsCompliantMode | Enables the FIPS-compliant operation mode. If you provide this parameter, the cmdlet will restrict connection to non-compliant platforms.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSecurityOptions object that contains Veeam Backup & Replication security settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Trust Policy for Linux Hosts

|  |  |
| --- | --- |
| This example shows how to modify the trust policy for Linux hosts.  |  | | --- | | $policy = Get-VBRLinuxTrustedHostPolicy  Set-VBRSecurityOptions -HostPolicy $policy |  Perform the following steps:   1. Run the [Get-VBRLinuxTrustedHostPolicy](get-vbrlinuxtrustedhostpolicy.md) cmdlet. Save the result to the $policy variable. 2. Run the Set-VBRSecurityOptions cmdlet. Set the $policy variable as the HostPolicy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Audit logs Settings

|  |  |
| --- | --- |
| This example shows how to modify audit logs settings. Veeam Backup & Replication will store logs in the C:\Users\Administrator\Documents\Logs folder.  |  | | --- | | Set-VBRSecurityOptions -AuditLogPath "C:\Users\Administrator\Documents\Logs" | |

Related Commands

* [Get-VBRSecurityOptions](get-vbrsecurityoptions.md)
* [Get-VBRLinuxTrustedHostPolicy](get-vbrlinuxtrustedhostpolicy.md)



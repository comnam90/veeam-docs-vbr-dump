---
title: "Set-VBRNodeExporterOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnodeexporteroptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRNodeExporterOptions


Short Description

Modifies node exporter metrics for Veeam Software Appliance

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNodeExporterOptions [-EnableMetricsSharing] [-EnableTLS] [-AuthType <VBRMetricsServerAuthType>] [-Username <String>] [-Password <String>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for node exporter metrics configured for Veeam Software Appliance.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| EnableMetricsSharing | Enables sharing of node exporter metrics.  Default: False. | SwitchParameter | False | Named | False |
| EnableTLS | Enables TLS encryption for node exporter metrics.  Default: False. | SwitchParameter | False | Named | False |
| AuthType | Specifies the authentication type that you want to use for sharing node exporter metrics:   * None — use this to skip authentication * Password —  use it to enable the password authentication.   Default: None. | VBRMetricsServerAuthType | False | Named | False |
| Password | Use this parameter when the AuthType parameter is set to Password.  Specifies the password for authenticating with the node exporter metrics endpoint. | String | False | Named | False |
| Username | Use this parameter when the AuthType parameter is set to Password.  Specifies the user name for authenticating with the node exporter metrics endpoint. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNodeExporterOptions object that contains Veeam Backup & Replication node exporter metrics sharing settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Node Exporter Metrics Sharing with Password Authentication

|  |  |
| --- | --- |
| This command enables sharing of node exporter metrics with the password authentication.  |  | | --- | | Set-VBRNodeExporterOptions -EnableMetricsSharing -AuthType Password -Username "admin" -Password "P@ssw0rd" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling TLS for Node Exporter Metrics Sharing

|  |  |
| --- | --- |
| This example enables sharing of node exporter metrics with the TLS encryption. Password authentication is not used.  |  | | --- | | Set-VBRNodeExporterOptions -EnableMetricsSharing -EnableTLS | |

Page updated 2026-06-24


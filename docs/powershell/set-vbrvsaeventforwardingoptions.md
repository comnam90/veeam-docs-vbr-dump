---
title: "Set-VBRVSAEventForwardingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvsaeventforwardingoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRVSAEventForwardingOptions


Short Description

Modifies Veeam Software Appliance syslog event forwarding settings.

Applies to

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRVSAEventForwardingOptions [-EnableSyslogForwarding] [-UseBackupServerSyslogOptions] [-ServerName <String>] [-Port <Int32>] [-TransportProtocol <VBRSyslogServerProtocol>] [-SeverityRules <VBRSyslogServerEventSeverity[]>] [-AdvancedFilters <VBRVSAEventForwardingFilteringRule[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Veeam Software Appliance syslog event forwarding settings. You can enable or disable forwarding, configure the target syslog server, choose to reuse the Veeam Backup & Replication server syslog options, and define the default severity levels and per-application filtering rules.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Note |
| You cannot specify the ServerName, Port, TransportProtocol, SeverityRules, AdvancedFilters, or UseBackupServerSyslogOptions parameters while syslog forwarding is disabled. Provide the EnableSyslogForwarding parameter to enable forwarding first. The UseBackupServerSyslogOptions parameter and the manual server parameters (ServerName, Port, TransportProtocol) are mutually exclusive. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| EnableSyslogForwarding | Enables syslog event forwarding for the Veeam Software Appliance. To disable forwarding, set the parameter value to $false. That is, EnableSyslogForwarding:$false. | SwitchParameter | False | Named | False |
| UseBackupServerSyslogOptions | Defines that the appliance will reuse the syslog server settings configured on the Veeam Backup & Replication server. When this parameter is set, you cannot specify the ServerName, Port or TransportProtocol parameters. | SwitchParameter | False | Named | False |
| ServerName | Specifies the DNS name or IP address of the syslog server to which appliance events will be forwarded. | String | False | Named | False |
| Port | Specifies the port number of the syslog server. Permitted values: 1–65535. | Int32 | False | Named | False |
| TransportProtocol | Specifies the transport protocol that the appliance will use to send messages to the syslog server. Accepted values:   * Udp * Tcp * Tls | [VBRSyslogServerProtocol](enums.md#VBRSyslogServerProtocol) | False | Named | False |
| SeverityRules | Specifies an array of severity levels that the appliance will forward by default. Specify a single value from the list — the appliance forwards events at that severity and higher. Accepted values:   * Emergency * Alert * Critical * Error * Warning * Notice * Informational * Debug | [VBRSyslogServerEventSeverity](enums.md#VBRSyslogServerEventSeverity)[] | False | Named | False |
| AdvancedFilters | Specifies the array of per-application filtering rules that override the default severity rules for specific applications or daemons. | Accepts the [VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md)[] object. To create this object, run the [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRVSAEventForwardingOptions](vbrvsaeventforwardingoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Veeam Software Appliance Syslog Forwarding to Dedicated Server

|  |  |
| --- | --- |
| This example shows how to enable Veeam Software Appliance syslog event forwarding to a dedicated syslog server using the TCP transport protocol.  |  | | --- | | Set-VBRVSAEventForwardingOptions -EnableSyslogForwarding -ServerName "syslog.tech.local" -Port 514 -TransportProtocol Tcp -SeverityRules Error |  Perform the following steps:   1. Run the Set-VBRVSAEventForwardingOptions cmdlet. Specify the following settings:  * Provide the EnableSyslogForwarding parameter. * Specify the ServerName parameter value. * Specify the Port parameter value. * Set the Tcp value as the TransportProtocol parameter value. * Set Error as the SeverityRules parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Reusing Backup Server Syslog Settings With Advanced Filter

|  |  |
| --- | --- |
| This example shows how to enable appliance syslog forwarding using the syslog server already configured on the Veeam Backup & Replication server, and add an advanced filtering rule for the sshd daemon.  |  | | --- | | $rule = New-VBRVSAEventForwardingFilteringRule -Application "sshd" -SeverityRules Error, Critical  Set-VBRVSAEventForwardingOptions -EnableSyslogForwarding -UseBackupServerSyslogOptions -AdvancedFilters $rule |  Perform the following steps:   1. Run the [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md) cmdlet. Specify the Application and SeverityRules parameter values. Save the result to the $rule variable. 2. Run the Set-VBRVSAEventForwardingOptions cmdlet. Specify the following settings:  * Provide the EnableSyslogForwarding parameter. * Provide the UseBackupServerSyslogOptions parameter. * Set the $rule variable as the AdvancedFilters parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Disabling Veeam Software Appliance Syslog Forwarding

|  |  |
| --- | --- |
| This example shows how to disable Veeam Software Appliance syslog event forwarding.  |  | | --- | | Set-VBRVSAEventForwardingOptions -EnableSyslogForwarding:$false |  Run the Set-VBRVSAEventForwardingOptions cmdlet. Set the EnableSyslogForwarding parameter value to $false. |

Related Commands

* [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md)
* [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md)

Page updated 2026-06-12


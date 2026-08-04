---
title: "VBRVSAEventForwardingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvsaeventforwardingoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRVSAEventForwardingOptions


Contains Veeam Software Appliance syslog event forwarding settings. The settings define the syslog server to which appliance events are forwarded, the transport protocol, and the severity levels and per-application filters that determine which events are sent.

Properties

Properties

| Property | Type | Description |
| SyslogForwardingEnabled | Boolean | Indicates whether syslog event forwarding for the Veeam Software Appliance is enabled. |
| UseBackupServerSyslogOptions | Boolean | Indicates whether the appliance reuses the syslog server settings configured for the Veeam Backup & Replication server. |
| ServerName | String | DNS name or IP address of the syslog server to which appliance events are forwarded. |
| Port | Int32 | Port number of the syslog server. |
| TransportProtocol | [VBRSyslogServerProtocol](enums.md#VBRSyslogServerProtocol) | Transport protocol used to send messages to the syslog server. Possible values:   * Udp * Tcp * Tls |
| SeverityRules | [VBRSyslogServerEventSeverity](enums.md#VBRSyslogServerEventSeverity)[] | Array of severity levels that are forwarded by default. Possible values:   * Emergency * Alert * Critical * Error * Warning * Notice * Informational * Debug |
| AdvancedFilters | [VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md)[] | Array of per-application filtering rules that override the default severity rules for specific applications or daemons. |

Related Commands

* [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md)
* [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md)

Page updated 2026-05-27


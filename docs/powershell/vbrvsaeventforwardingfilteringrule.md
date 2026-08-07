---
title: "VBRVSAEventForwardingFilteringRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvsaeventforwardingfilteringrule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRVSAEventForwardingFilteringRule


Contains an advanced filtering rule for Veeam Software Appliance syslog event forwarding. The rule specifies which severity levels are forwarded for a specific application or daemon.

Properties

Properties

| Property | Type | Description |
| Application | String | Name of the application or daemon to which the rule applies. |
| Severity | [VBRSyslogServerEventSeverity](enums.md#VBRSyslogServerEventSeverity)[] | Array of severity levels that are forwarded for the application. Possible values:   * Emergency * Alert * Critical * Error * Warning * Notice * Informational * Debug |

Related Commands

* [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md)
* [Set-VBRVSAEventForwardingFilteringRule](set-vbrvsaeventforwardingfilteringrule.md)
* [Export-VBRVSAEventForwardingFilteringRule](export-vbrvsaeventforwardingfilteringrule.md)
* [Import-VBRVSAEventForwardingFilteringRule](import-vbrvsaeventforwardingfilteringrule.md)
* [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md)

Page updated 2026-05-27


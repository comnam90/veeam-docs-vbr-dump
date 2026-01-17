---
title: "Configuring Global SNMP Settings Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/general_snmp_settings_web.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Configuring Global SNMP Settings Using Web UI


To configure global SNMP settings, do the following in the Veeam Backup & Replication web UI:

1. Click the gear icon in the top bar.
2. Click the Event Forwarding tab.
3. In the SNMP Servers tab, click New.
4. In the Receiver field, specify an IPv4 or IPv6 address of the SNMP recipient. Note that you can use IPv6 addresses only if IPv6 communication is enabled as described in section [IPv6 Support](ipv6.md).
5. In the Port field, enter the port number to be used.
6. In the Community string field, enter the community identifier.
7. Click OK.

To edit the existing server, use the check box before the required server name, click Edit and make all necessary changes.

[![Configuring Global SNMP Settings Using Web UI](images/settings_snmp_servers.webp)](images/settings_snmp_servers.webp)



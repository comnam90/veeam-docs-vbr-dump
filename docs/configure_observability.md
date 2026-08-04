---
title: "Configuring 3rd Party Monitoring"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configure_observability.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring 3rd Party Monitoring


Veeam Backup & Replication can share appliance data with 3rd party monitoring tools. It shares performance metrics and forwards system logs from the Veeam Software Appliance and Veeam Infrastructure Appliances. This lets you monitor the health and resource consumption of the appliances in your backup infrastructure.

Veeam Backup & Replication uses the following native Linux tools:

* Node Exporter — shares appliance metrics in the Prometheus format.
* Syslog — forwards appliance system logs to a remote syslog server.

Veeam Backup & Replication distributes the configuration to all appliances every 5 minutes.

Consider the following:

* To use this functionality, you must have a Veeam Universal License (VUL) or an NFR license.
* You cannot customize the set of metrics that Node Exporter shares.

In This Section

* [Configuring Node Exporter](configure_node_exporter.md)
* [Configuring Syslog](configure_rsyslog.md)

Page updated 2026-07-01


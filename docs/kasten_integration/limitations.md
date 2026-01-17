---
title: "Limitations and Considerations"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/limitations.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---


In this article

Consider the following limitations for Veeam Backup & Replication:

* Veeam Plug-In for Kasten does not support Kerberos for Kasten exports to Veeam backup repositories.
* Veeam Plug-In for Kasten does not support IPv6.
* Veeam Plug-In for Kasten does not sync Veeam Kasten retention (retire) sessions.
* A Veeam Kasten instance can operate with only one backup server. If you add it to another backup server, you will not be able to perform any operations with this Veeam Kasten instance on the first backup server.
* Veeam Plug-In for Kasten does not support Kasten exports to direct backup object storage repositories.
* If you delete Veeam Kasten policies created by the Veeam Kasten Multi-Cluster console on Kasten secondary servers, they will be recreated by the Veeam Kasten Multi-Cluster console.
* Veeam Plug-In for Kasten does not support Kasten export from Kasten instance that is not added to the Veeam Backup & Replication infrastructure.
* Veeam Plug-In for Kasten is not supported in the Veeam Backup & Replication web UI.
* If you work with Veeam Backup & Replication on Linux, you cannot use domain user for location profiles in Veeam Kasten.

Page updated 11/28/2025

Page content applies to build 13.0.1.1071

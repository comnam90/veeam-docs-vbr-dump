---
title: "Before You Begin"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_remote_console_byb.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you use the Remote Access Console to connect to the tenant backup server, complete the following prerequisites:

* Connection with the Remote Access Console to the tenant backup server is possible only if the SP and tenant backup servers have the same build number and the same private fixes of Veeam Backup & Replication installed. Build numbers of Veeam Backup & Replication plug-ins must be the same as well. If the build numbers or private fixes differ, remote connection to the tenant backup server may be established over the Remote Desktop Protocol. To learn more, see [Launching Remote Desktop Session to Tenant](cc_remote_desktop.md).

* The tenant must enable the Allow this Veeam Backup & Replication installation to be managed by the service provider option in the Service Provider wizard when connecting to the SP. To learn more, see [Specify Cloud Gateway Settings](cloud_connect_sp_settings.md).
* If the machine on which you plan to use the Remote Access Console does not reside in the SP backup infrastructure network, you need to set up Veeam Backup & Replication to accept connections from the Remote Access Console over the internet. To learn more, see [Enabling Access to Cloud Gateway](cc_remote_access.md).



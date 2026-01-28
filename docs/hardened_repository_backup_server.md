---
title: "Using Backup Server as Immutable Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_backup_server.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Using Backup Server as Immutable Repository


If you use a Veeam Software Appliance as a backup server, it can be used as an immutable repository without additional preparation. This provides similar functionality to a hardened repository on a dedicated server.

However, due to the presence of additional services and fewer restrictions, using a backup server as a immutable repository increases the attack surface of your backup infrastructure. For medium-sized and large-scale environments, it is recommended to deploy a hardened repository on a dedicated server.



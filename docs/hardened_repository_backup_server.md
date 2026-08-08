---
title: "Using Backup Server as Immutable Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_backup_server.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Using Backup Server as Immutable Repository


If you use a Linux-based backup server, it acts as an immutable repository without additional preparation. This provides similar functionality to a hardened repository on a dedicated server.

However, due to the presence of additional services and fewer restrictions, using a backup server as a immutable repository increases the attack surface of your backup infrastructure. For medium-sized and large-scale environments, it is recommended to deploy a hardened repository on a dedicated server.

Page updated 2026-08-06


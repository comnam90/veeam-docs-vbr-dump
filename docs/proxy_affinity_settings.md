---
title: "Specifying Proxy Affinity Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/proxy_affinity_settings.html"
last_updated: "2/22/2024"
product_version: "13.0.1.1071"
---

# Specifying Proxy Affinity Settings


For every backup repository, you can configure proxy affinity settings — define a list of backup proxies that can work with this backup repository. Proxy affinity binds backup proxies to specific backup repositories. When transporting data to/from the backup repository, Veeam Backup & Replication tries to pick a VMware backup proxy from the proxy affinity list whenever it is possible.

To configure a proxy affinity list for a backup repository:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Backup Repositories.
3. In the working area, select the backup repository and click Proxy Affinity on the ribbon or right-click the backup repository and select Proxy affinity.
4. In the Proxy Affinity window, select Prefer the following backup proxies for this repository and select check boxes next to the backup proxies that you want to bind to the backup repository.

[![Click to zoom in](images/proxy_affinity.webp)](images/proxy_affinity.webp "Click to zoom in")

Related Topics

[Proxy Affinity](proxy_affinity.md)



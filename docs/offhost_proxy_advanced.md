---
title: "Configuring Advanced Options for Off-Host Backup Proxies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/offhost_proxy_advanced.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Configuring Advanced Options for Off-Host Backup Proxies


When you configure a backup or replication job, you can instruct Veeam Backup & Replication to automatically assign an off-host backup proxy to the job. To select an appropriate off-host backup proxy, Veeam Backup & Replication uses a static topology scheme — a scheme of available connections in the backup infrastructure. The static topology scheme is updated once in 4 hours, when Veeam Backup & Replication performs automatic rescan of backup infrastructure components.

In some situations, the static topology scheme may not be enough. In some storage systems (for example, iSCSI SAN), the hardware VSS provider configures connections to volume snapshots on the fly. When a volume snapshot is created, the hardware VSS provider automatically creates a new target for the volume snapshot or enables a connection to the volume snapshot for the off-host backup proxy.

In such case, the mechanism of automatic off-host backup proxy detection will not work properly. To overcome this situation, you can manually present volumes to the off-host backup proxy and assign the necessary off-host backup proxy to the job.

In This Section

* [Presenting Volumes to Off-Host Backup Proxies](present_volumes.md)
* [Assigning Off-Host Backup Proxies to Jobs](assign_proxy.md)



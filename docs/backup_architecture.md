---
title: "Backup Infrastructure for Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_architecture.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Backup Infrastructure for Backup

In this article

Veeam Backup & Replication uses the following components for the backup process:

* One or more source hosts with associated datastores
* One or more backup proxies
* Backup repository
* [Optional] One or more guest interaction proxies
* [For shared folder backup repository] Gateway server

All backup infrastructure components engaged in the job make up a data pipe. The source host and backup repository produce two terminal points for the data flow. Veeam Backup & Replication processes VM data in multiple cycles, moving VM data over the data pipe block by block.

Veeam Backup & Replication collects VM data, transforms and transports it to the target with the help of [Veeam Data Movers](veeam_transport_service.md). Veeam Backup & Replication uses two-service architecture — one Veeam Data Mover controls interaction with the source host and the other controls interaction with the backup repository. Veeam Data Movers communicate with each other and maintain a stable connection.

When a new backup session starts, Veeam Backup & Replication performs the following actions:

1. Veeam Backup & Replication deploys non-persistent runtime components or, if necessary, persistent agent components on VM guest OSes using the guest interaction proxy (for Microsoft Windows VMs) or backup server (for VMs with other OSes).
2. The target-side Veeam Data Mover obtains job instructions and communicates with the source-side Veeam Data Mover to begin data collection.
3. The source-side Veeam Data Mover copies VM data from the source storage in one of the transport modes. During incremental job runs, the source-side Veeam Data Mover retrieves only those data blocks that have changed since the previous job session.

While copying, the source-side Veeam Data Mover performs additional data processing. It filters out zero data blocks, blocks of swap files and blocks of excluded VM guest OS files; it compresses and deduplicates VM data blocks and moves them to the target-side Veeam Data Mover.

1. The target-side Veeam Data Mover deduplicates similar blocks of data on the target side and writes the result to the backup file in the backup repository.

On-Site Backup

To back up to a Microsoft Windows or Linux-based backup repository in the local site, you need to deploy a backup proxy on a machine with access to the source datastore and point the backup job to this backup proxy. In this scenario, the source-side Veeam Data Mover is started on the backup proxy, and the target-side Veeam Data Mover is started on the Microsoft Windows or Linux repository. VM data is sent from the backup proxy to the backup repository over the LAN.

![Backup Infrastructure for Backup](images/onsite_backup_repo_vmware.webp)

To back up to a shared folder in the local site, you need to deploy a gateway server with access to the shared folder backup repository. You can assign the role of a gateway server to the backup server itself or any Microsoft Windows machine added to the backup infrastructure.

You can use the same Microsoft Windows machine as the backup proxy and gateway server for SMB. In this scenario, Veeam Backup & Replication starts the source-side and target-side Veeam Data Movers on the same machine and sends VM data from the backup proxy to the shared folder backup repository over the LAN.

![Backup Infrastructure for Backup](images/onsite_backup_share_vmware.webp)

Off-Site Backup

The common requirement for off-site backup is that one Veeam Data Mover runs in the production site (closer to the source datastore), and the other Veeam Data Mover runs in the remote site, closer to the backup repository. During backup, Veeam Data Movers maintain a stable connection, which allows for uninterrupted operation over the WAN or slow links.

To back up to a Microsoft Windows or Linux repository in the remote site, you need to deploy a backup proxy in the production site, closer to the source datastore. In this scenario, the source-side Veeam Data Mover is started on the backup proxy, and the target-side Veeam Data Mover is started on the Microsoft Windows or Linux repository. VM data is sent from the backup proxy to the backup repository over the WAN.

![Backup Infrastructure for Backup](images/offsite_backup_repo_vmware.webp)

To back up VMs to a shared folder backup repository in the remote site, you must deploy a backup proxy in the source site and a gateway server in the remote site. The shared folder backup repository must be pointed at the target-side gateway server. During backup, the source-side Veeam Data Mover is started on the source backup proxy in the production site, and the target‑side Veeam Data Mover is started on the target gateway server in the remote site. VM data is transferred between the backup proxy and gateway server over the WAN.

![Backup Infrastructure for Backup](images/offsite_backup_share_vmware.webp)

Related Topics

* [Backup Infrastructure Components](components.md)
* [Data Compression and Deduplication](compression_deduplication.md)

Page updated 9/5/2025

Page content applies to build 13.0.1.1071

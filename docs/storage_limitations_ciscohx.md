---
title: "Cisco HyperFlex"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_limitations_ciscohx.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Cisco HyperFlex


If you plan to use VMware integration and perform backup and replication from Cisco HyperFlex storage snapshots, consider the following:

* The availability of the feature depends on the license you use. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).

* Cisco HyperFlex system must be added to the backup infrastructure. For more information, see [Adding Cisco HyperFlex Storage System](cisco_add.md).

* VMs must be hosted on the supported Cisco HyperFlex system. For more information, see the [System Requirements](storage_system_requirements.md) section in the Veeam Backup & Replication User Guide.

* Only infrastructure rescan is supported. For more information on rescan, see [Rescanning Storage Systems](storage_rescan.md).
* Proxy must be properly configured in the backup infrastructure. For more information, see [Configuring Proxies](cisco_backup_proxy.md).

* VMs must not have VMware snapshots created using traditional ESXi snapshot technology. Snapshots created using the NFS native snapshot technology may be present.

During backup or replication, Veeam Backup & Replication fails to trigger Cisco HyperFlex snapshots on VMs that already have VMware snapshots created using traditional ESXi snapshot technology. You can instruct Veeam Backup & Replication to process these VMs in the regular data processing mode. To do this, enable the Failover to standard backup option in job settings.

* The Limit processed VM count per storage snapshots to N option is not applicable to Cisco HyperFlex since snapshots for VMs hosted on Cisco HyperFlex are created at the VM level, not volume level.
* For working with REST API, use default route and default port: https://{hostname}:443.



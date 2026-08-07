---
title: "Active Directory Forest Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ad_forest_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Active Directory Forest Restore


Veeam Backup & Replication lets you recover an entire Active Directory forest after a failure that affects all domain controllers, for example, Active Directory schema corruption or a ransomware attack on the domain controllers. Veeam Backup & Replication can create image-level backups of the domain controllers and then orchestrate and automate the full forest recovery.

Recovering an Active Directory forest manually with native tools is a complex, multi-step process that can take a long time to complete. For more information on the manual forest recovery process, see the [Active Directory Forest Recovery Guide](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-guide).

Veeam Backup & Replication follows the Microsoft forest recovery process while simplifying the planning and preparation. Through orchestration and automation of the recovery steps, Veeam Backup & Replication reduces the time and effort required to bring the forest back online.

Veeam Backup & Replication supports any forest structure: single-domain, multi-domain and multi-tree forests.

In this version, you can restore from VMware vSphere and Microsoft Hyper-V backups to either of these two platforms. Cross-platform restore is supported — for example, a backed-up domain controller running on VMware vSphere can be restored to Microsoft Hyper-V, and the other way around.

In This Section

* [How Active Directory Forest Restore Works](ad_forest_restore_hiw.md)
* [Before You Begin](ad_forest_restore_byb.md)
* [Restoring Active Directory Forest to VMware vSphere](restore_ad_forest_vm.md)
* [Restoring Active Directory Forest to Microsoft Hyper-V](restore_ad_forest_hv.md)
* [Post-Restore Actions](restore_ad_forest_post_restore.md)

Page updated 2026-07-31


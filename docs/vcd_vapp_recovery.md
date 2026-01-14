---
title: "vApp Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_vapp_recovery.html"
last_updated: "8/30/2023"
product_version: "13.0.1.1071"
---

# vApp Recovery

In this article

With vApp recovery, you can restore the whole vApp from a backup to VMware Cloud Director.

vApps can be restored to their organization VDC or to any other organization VDC. You can restore the vApp that already exists, for example, in case the vApp is corrupted or you want to revert to an earlier state of the vApp, or the vApp that no longer exists, for example, if it was deleted by mistake. If you restore a vApp that already exists, the vApp is overwritten with that from the VMware Cloud Director backup.

During vApp recovery, Veeam Backup & Replication recovers VMs within one vApp one by one consequently. vApps are recovered in parallel.

|  |
| --- |
| Important |
| You can restore only those VMs whose placement policy is the same as the default placement policy of the target organization VDC (VDC where the vApp to which you restore VMs reside). For more information on placement policies, see [VMware Docs](https://docs.vmware.com/en/VMware-Cloud-Director/10.4/VMware-Cloud-Director-Service-Provider-Admin-Portal-Guide/GUID-38C72A2B-B5CA-475C-A154-ACD4C4C475CC.html). |

Page updated 8/30/2023

Page content applies to build 13.0.1.1071

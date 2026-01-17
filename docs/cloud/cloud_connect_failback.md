---
title: "Failback"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_failback.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Failback


If a tenant wants to resume operation of a production VM, they can fail back to it from a VM replica on the cloud host. When you perform failback, you get back from the VM replica to the original VM, shift your I/O and processes from the cloud host to the source production host and return to the normal operation mode.

A tenant can perform failback to a production VM after partial site failover or full site failover. If a tenant performs the failback operation after full site failover, they need to process every VM in the cloud failover plan individually.

If a tenant managed to restore operation of the source host at the production site, a tenant can switch from the VM replica to the original VM on the source host. If the source host is not available, a tenant can restore the original VM to a new location and switch back to it.

* To learn more about failback for snapshot-based replicas, see the [Failover and Failback for Replication: Failback](https://helpcenter.veeam.com/docs/vbr/userguide/failback.html?ver=13) section in the Veeam Backup & Replication User Guide.
* To learn more about failback for CDP replicas, see the [Failover and Failback for CDP: Failback](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_failback.html?ver=13) section in the Veeam Backup & Replication User Guide.

Failback to production is a temporary stage that should be further finalized. After a tenant tests the recovered original VM and make sure it is working without problems, they should commit failback. A tenant also has an option to undo failback and return the VM replica back to the Failover state.

The failback operation is available on the tenant side only. The SP cannot perform failback for tenant VM replicas in the SP Veeam backup console.



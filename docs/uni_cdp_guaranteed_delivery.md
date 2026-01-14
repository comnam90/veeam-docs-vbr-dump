---
title: "Guaranteed Delivery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_guaranteed_delivery.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Guaranteed Delivery

In this article

In CDP, data delivery between any two backup infrastructure components is guaranteed by means of the TCP protocol. However, there can be situations when Veeam Backup & Replication is not able to send all data changes generated during CDP in time. For example, if RPO is small, a VM generates a lot of changes, but the infrastructure performance is not enough; or a CDP proxy gets out of work because of a power outage, and all data changes stored on it are lost. This makes data inconsistent and leads to the loss of restore points.

CDP has a special mechanism and tools that return data into the consistent state. The I/O filter on the source host has a mechanism that tracks data blocks that have changed — change tracking (CT). The I/O filter deletes data block addresses from the list of changed blocks only after a confirmation message that data blocks were successfully saved to the replica is received from the target host. In addition, CDP proxies also store data changes until a confirmation message is received from the target host.

How Veeam Backup & Replication uses these tools depend on whether issues occur on the source or target site:

* Source site. If the source host does not send the data changes because of the high system load, Veeam Backup & Replication waits till the load decreases. And only then, it gets the list of changed data blocks, reads data blocks from the disk and sends the data to the target host. The target host saves the received data to the datastore. Until this moment, the data on the target host remains inconsistent. As a result, there are "gaps" in the restore point journal and you are not able to restore a VM to some points in time. However, after the target host saves the data, the CDP policy resumes the creation of consistent restore points.

If the source proxy gets out of work, Veeam Backup & Replication selects another CDP proxy and then behaves as described in the previous paragraph, except for waiting for the load decrease.

* Target site. If the target proxy gets out of work, Veeam Backup & Replication selects another CDP proxy and requests data changes from the source CDP proxy. The proxy sends the changes to the target host once again, and the data on the target host becomes consistent almost immediately, so that you are able to restore a VM to any point in time.

If the connection between the target CDP proxy and the target host is lost, Veeam Backup & Replication checks the host state. If the host is in the Maintenance mode or has disappeared from the cluster, Veeam Backup & Replication starts writing data changes to replicas using another target ESXi host (provided that the host exists and is connected to the datastore where replicas are stored). If the host is not in the Maintenance mode or has not disappeared, Veeam Backup & Replication considers that these are temporary problems with the network and sends data changes again after some time.

Page updated 10/17/2025

Page content applies to build 13.0.1.1071

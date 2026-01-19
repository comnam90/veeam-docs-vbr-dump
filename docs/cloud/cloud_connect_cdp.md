---
title: "Continuous Data Protection (CDP) with Veeam Cloud Connect"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_cdp.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Continuous Data Protection (CDP) with Veeam Cloud Connect


SPs can use the continuous data protection (CDP) functionality to offer Disaster Recovery as a Service to tenants. CDP extends Veeam Cloud Connect Replication scenarios with an option to create replicas without creating snapshots. This allows the SP to protect mission-critical tenant machines for which data loss is unacceptable: compared to snapshot-based replication, CDP provides near-zero recovery time objective (RTO) because CDP replicas are in a ready-to-start state.

Veeam Cloud Connect supports the following types of the CDP technology offered by Veeam Backup & Replication:

* [CDP for VMware vSphere](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_replication.html?ver=13)
* [Universal CDP to VMware vSphere](https://helpcenter.veeam.com/docs/vbr/userguide/universal_cdp.html?ver=13)

CDP with Veeam Cloud Connect is in many ways similar to both CDP in the regular Veeam Backup & Replication infrastructure and snapshot-based Veeam Cloud Connect Replication.

* CDP in the Veeam Cloud Connect environment uses vSphere APIs for I/O filtering (VAIO) in the same way as regular CDP. The general concept of CDP is similar as well: Veeam Backup & Replication maintains the CDP infrastructure and performs continuous data replication of tenant machines. To learn more about CDP mechanisms in Veeam Backup & Replication, see the [Continuous Data Protection (CDP) for VMware vSphere](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_replication.html?ver=13) and [Universal CDP to VMware vSphere](https://helpcenter.veeam.com/docs/vbr/userguide/universal_cdp.html?ver=13) sections in the Veeam Backup & Replication User Guide.

* CDP in the Veeam Cloud Connect environment supports data protection and disaster recovery scenarios similar to snapshot-based Veeam Cloud Connect Replication, and offers similar workflow. The SP allocates computing, storage and network resources and provides them to tenants through hardware plans or organization VDCs in VMware Cloud Director. CDP has a multi-tenant architecture; CDP infrastructure components are distributed between the tenant side and SP side, and communicate through the cloud gateway.

To use CDP with Veeam Cloud Connect, the SP and tenants must configure the CDP infrastructure on their sides. After that, tenants can create CDP policies targeted at a cloud host. In case a disaster strikes, the tenant can fail over a group of production machines or individual machines to CDP replicas on the cloud host.

In This Section

* [Veeam Cloud Connect CDP Scenarios](cloud_connect_cdp_scenarios.md)
* [CDP Infrastructure in Veeam Cloud Connect](cloud_connect_cdp_infrastructure.md)
* [Getting Started with CDP](cloud_connect_cdp_quickstart.md)
* [Failover and Failback for CDP](cloud_cdp_failover_and_failback.md)

Related Topics

* [Veeam Cloud Connect Replication](cloud_replication.md)
* [VMware Cloud Director Support](cloud_vcloud_director.md)
* [Considerations and Limitations for CDP](cloud_replication_limitations.md#cdp)



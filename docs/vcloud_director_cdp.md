---
title: "CDP for VMware Cloud Director"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_cdp.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# CDP for VMware Cloud Director

In this article

Continuous data protection (CDP) for VMware Cloud Director is a technology that helps you protect mission-critical vApps and VMs when data loss for seconds or minutes is unacceptable. CDP also provides minimum recovery time objective (RTO) in case a disaster strikes because CDP replicas are in a ready-to-start state.

CDP for VMware Cloud Director utilizes a similar mechanisms as CDP for VMware vSphere VMs. The main difference is that the unit for replication and failover is a vApp, not a VM. For more information on CDP for VMware vSphere VMs, see [Continuous Data Protection (CDP)](cdp_replication.md).

To protect vApps using CDP for Cloud Director, you first need to configure the infrastructure and then to create a Cloud Director CDP policy. For more information, see [Backup Infrastructure for Cloud Director CDP](vcloud_director_cdp_infrastructure.md) and [Creating Cloud Director CDP Policies](vcd_cdp_policies_create.md). To recover vApps to a short-term or long-term restore point, you need to fail over to its replica. For more information, see [Failover and Failback for Cloud Director CDP](vcd_cdp_failover_failback.md).

Related Topics

* [Continuous Data Protection (CDP)](cdp_replication.md)
* [Continuous Data Protection (CDP) with Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_cdp.html?ver=13)

In This Section

* [Backup Infrastructure for Cloud Director CDP](vcloud_director_cdp_infrastructure.md)
* [Requirements and Limitations](vcloud_director_cdp_req.md)
* [How Cloud Director CDP Works](vcloud_director_cdp_hiw.md)
* [Installing I/O Filter on VDCs](vcloud_director_cdp_io_filter_install.md)
* [Updating and Uninstalling I/O Filter](vcd_cdp_io_filter_uninstall.md)
* [Creating Cloud Director CDP Policies](vcd_cdp_policies_create.md)
* [Managing Cloud Director CDP Policies](vcd_cdp_manage_policies.md)
* [Managing Cloud Director CDP Replicas](vcd_cdp_replica_manage.md)
* [Failover and Failback for Cloud Director CDP](vcd_cdp_failover_failback.md)

Page updated 10/22/2025

Page content applies to build 13.0.1.1071

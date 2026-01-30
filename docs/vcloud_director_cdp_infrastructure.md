---
title: "Backup Infrastructure for Cloud Director CDP"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_cdp_infrastructure.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Backup Infrastructure for Cloud Director CDP


The following backup infrastructure components are required for VMware Cloud Director CDP:

* [Backup server](#backup_server)
* [Source and Target organization VDCs](#vdc)
* [CDP proxies](#cdp_proxies)

Backup Server

The backup server is the configuration, administration and management core of the backup infrastructure. The backup server runs the Veeam CDP Coordinator Service. This service coordinates replication and data transfer tasks, and controls resource allocation. We recommend that you place the backup server in the target site or as a separate unit.

For more information on the backup server, see [Backup Server](backup_server.md).

Source and Target Organization VDCs

The source and the target organization VDCs are two terminal points between which replicated vApp and VM data is moved. The source and target organization VDCs must be a part of one VMware Cloud Director server or two different servers. In the underlying VMware vSphere infrastructure, hosts must be added to clusters managed by vCenter Servers. For more information on the requirements to the infrastructure and how to add Cloud Director servers, see [Requirements and Limitations](vcloud_director_cdp_req.md) and [Adding VMware Cloud Director Servers](adding_vcloud_director.md).

The source and target VDC organizations perform the following tasks:

* The source organization VDC reads vApp and VM disk data, reads and processes I/O operations and sends data to source CDP proxies. The data is sent uncompressed.
* The target organization VDC receives data from target CDP proxies and saves this data to replicas on the datastore. Also, the target VDC manages replicas: creates replicas, retains restore points and so on.

I/O Filter on Organization VDCs

To be able to use organization VDCs for CDP, you must install the I/O filter on each VDC where vApps reside. After you install the I/O filter on the organization VDCs, Veeam Backup & Replication automatically installs the filter on all underlying clusters and their hosts. For more information on how to install the filter, see [Installing I/O Filter on VDCs](vcloud_director_cdp_io_filter_install.md).

It is the I/O filter that reads and processes I/O operations between the protected vApps and their underlying datastore and that sends and receives data from CDP proxies. Also, the filter communicates with the Veeam CDP Coordinator Service on the backup server and notifies the service that the backup infrastructure must be reconfigured if any proxy becomes unavailable. This I/O filter is built on the basis of vSphere API for I/O filtering (VAIO).

CDP Proxies

A CDP proxy is a component that operates as a data mover and transfers data between the source and target organization VDCs. We recommend that you configure at least two CDP proxies: one (source proxy) in the production site and one (target proxy) in the disaster recovery site.

The source and target CDP proxies perform the following tasks:

* The source proxy prepares data for short-term restore points from data received from the source host, compresses and encrypts the data (if encryption is enabled in the [network traffic rules](internet_rule.md)). Then sends it to the target proxy.
* The target proxy receives the data, decompresses and decrypts it, and then sends to the target host.

For more information on CDP proxies, their requirements, limitations and deployment, see [CDP Proxies](cdp_proxy.md).



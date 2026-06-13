---
title: "Resource Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_resource_planning.html"
last_updated: "6/10/2026"
product_version: "13.0.2.29"
---

# Resource Planning


Before you protect your environment with Veeam Plug-In, plan the resources for the components of your backup infrastructure.

Backup Server

In addition to the [general system requirements for the backup server](system_requirements_backup_server.md), we recommend adding an extra 1 CPU core and 2.5 GB RAM to your configuration for every 5 machines protected with Veeam Plug-Ins for Enterprise Applications.

Backup Repository

Ensure that the number of available task slots on the Veeam backup repository matches the number of channels (data streams) that you want to run concurrently. By default, Veeam Plug-In uses one channel per data backup operation. You can configure Veeam Plug-In to use multiple channels if needed. Using multiple channels channels in the backup process improves overall backup performance because Veeam Plug-In distributes the data equally across available channels. At the same time, using multiple channels increases resources consumption on the server with Veeam Plug-In installed, the network and the Veeam backup repository.

The number of configured channels must be equal to the number of available task slots in the repository because each parallel channel consumes one task slot. To learn more about resource usage and limitations, see [Resource Scheduling](resource_scheduling.md).

Database Server

Resource consumption on the server with Veeam Plug-In installed depends primarily on the achieved backup throughput. Actual throughput can be limited by source storage I/O performance, network bandwidth, or target storage I/O performance.

We recommend planning for 1 to 3 CPU cores and 0.5 to 1 GB RAM of resource consumption on the server with Veeam Plug-In for every 1 GB/s of achieved backup throughput. CPU consumption within the specified range depends on the compression and encryption settings. For example, source-side compression and encryption increase CPU usage.

Recommended resource values were measured on 3rd Generation Intel Xeon Scalable processors. Newer processor generations typically require fewer resources, while older processor generations may require more resources.



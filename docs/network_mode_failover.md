---
title: "Failover to Network Mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/network_mode_failover.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Failover to Network Mode

In this article

You can instruct Veeam Backup & Replication to switch to the Network transport mode and transfer VM data over LAN if the primary transport mode — Direct storage access or Virtual appliance — fails during the job session. This option is enabled by default to ensure that jobs and tasks can be completed successfully in any situation. In scenarios when the data cannot be processed by other transport modes, failover to the Network transport mode applies automatically even if the failover option is disabled.

Note that data transport over LAN puts additional load on your production network and may potentially affect performance if you accomplish data protection and disaster recovery tasks in business hours.

![Failover to Network Mode](images/failover_to_network.webp)

Page updated 6/27/2024

Page content applies to build 13.0.1.1071

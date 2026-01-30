---
title: "Configuring Performance Throttling"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plan_and_manage_performance_throttling_sap.html"
last_updated: "11/25/2025"
product_version: "13.0.1.1071"
---

# Configuring Performance Throttling


You can limit computer processing (CPU) resources assigned for Veeam Plug-In backup jobs. This setting allows you to reduce the impact of backup operations on the target computer performance. Performance throttling prevents Veeam Plug-Ins from utilizing all computer resources to ensure that enough resources are provided for other operations. This maybe useful in case you detected that your source database responses are slower during backup operations.

If you throttle performance, Veeam Backup & Replication starts Veeam Plug-In backup operation processes with low priority and nice value of 19. The nice values are in ascending order of priority ranging from -20 (the highest priority) to 19 (the lowest priority). Keep in mind that Veeam Plug-Ins manage the priority of backup operation processes only if the system running on the target computer is busy with other tasks.

|  |
| --- |
| Note |
| * By default, Veeam Plug-In does not throttle performance. * Performance throttling does not apply to restore operations. |

To throttle Veeam Plug-In performance, do the following:

1. Log into the machine with a user with root or instance owner privileges.
2. Start the Veeam Plug-In configuration tool with the following parameter:

|  |
| --- |
| SapOracleBackintConfigTool --set-throttling |

1. To confirm that you want Veeam Plug-In throttle performance, type y.

|  |
| --- |
| All backup activities will be throttled if the system is busy. Backup performance may be affected. Proceed? (y/N): y |



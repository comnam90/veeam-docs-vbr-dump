---
title: "Configuring Parallelism for Redo Logs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_parallelism.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Configuring Parallelism for Redo Logs

In this article

To configure backup or restore of redo logs through multiple channels, you can change the parallelism parameter in the Veeam configuration XML file as follows:

1. On the machine with Veeam Plug-In, open the /opt/veeam/VeeamPluginforSAPOracle/veeam\_config.xml file.
2. Set the necessary values for the parallelism values:

|  |
| --- |
| <PluginParameters Parallelism="4" LogsParallelism="4" /> |

where:

* the LogsParallelism parameter defines the number of parallel channels for backup and restore of redo logs
* the Parallelism parameter configures the parallelism for backup and restore of Oracle datafiles. This setting is configured in the [Veeam Plug-In configuration wizard](configure_sap_orcl.md)

Keep in mind that you must add parameters to the existing line in the veeam\_config.xml file. If you create a new line with the same name as the existing line, Veeam Plug-In will consider parameters only in the first detected line. Other parameters will be ignored.

Page updated 4/4/2025

Page content applies to build 13.0.1.1071

---
title: "Specifying SNMP Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/snmp_settings.html"
last_updated: "8/5/2025"
product_version: "13.0.1.1071"
---

# Specifying SNMP Settings


You can receive SNMP traps with results on jobs performed on the backup server. You can use SNMP traps to feed data to other monitoring systems such as CA Unicenter, BMC Patrol, IBM Tivoli or HPE OneView. SNMP traps can be sent to 5 different destinations.

Veeam Backup & Replication supports SNMP versions 1 and 2 (including including v2c and v2p).

|  |
| --- |
| Tip |
| You can find the list of available SNMP traps in the VeeamBackup.mib file. The remote Veeam Backup & Replication console stores this file in the <vbr\_installation\_folder>\Console\ folder. To interpret the traps incoming from the backup server, import the VeeamBackup.mib file to your recipient systems. |

To receive SNMP traps, you must perform the following tasks:

* Configure global SNMP settings either in the [Veeam Backup & Replication console](general_snmp_settings.md) or in the [Veeam Backup & Replication web UI](general_snmp_settings_web.md).
* [Configure SNMP service properties](snmp_service_properties.md).
* [Configure SNMP settings for jobs](job_snmp_settings.md).



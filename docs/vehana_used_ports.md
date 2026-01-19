---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_used_ports.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Ports


The following table lists network ports that must be opened for managing SAP HANA data restore. For more information on the ports used for data transfer during recovery, see the [Ports](ports_vpsh.md) section for standalone plug-ins or the [Ports](plan_and_manage_used_ports.md) section for managed plug-ins.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Backup server | SAP Web Services | TCP | 1129, 5<xx>14 where <xx> is the number of the instance | Ports used for establishing an HTTPS (SSL) connection to SAP Web Services. Port 1129 is used by the SAP Control web service and port 5<xx>14 is used by the SAP Start web service. |
| 1128, 5<xx>13 where <xx> is the number of the instance | Ports used for establishing an HTTP connection to SAP Web Services. Port 1128 is used by the SAP Control web service and port 5<xx>13 is used by the SAP Start web service. |
| Target SAP HANA System | TCP | 3<xx>13 where <xx> is the number of the instance | Port used for establishing a connection to the target SAP HANA system database when restoring tenant databases. |



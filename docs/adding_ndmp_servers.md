---
title: "Adding NDMP Servers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/adding_ndmp_servers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding NDMP Servers


To back up volumes from NAS devices by the NDMP protocol, you must add the device as an NDMP server.

|  |
| --- |
| Note |
| Before you add a NetApp NDMP server to the tape infrastructure, you must add the NDMP storage system to Veeam Backup & Replication and enable the NDMP server role at the Name step of the New NetApp ONTAP Storage wizard. For more details, see [Adding NetApp ONTAP](netapp_add.md). |

To add an NDMP server or a NetApp NDMP server with SMTape support, follow the next steps:

1. [Launch the New NDMP Server wizard](ndmp_server_launch.md).
2. [Select connection mode](ndmp_server_type.md).
3. [Specify an NDMP server name and credentials](ndmp_server_server_types.md).
4. [Specify connection settings](ndmp_server_connection.md).
5. [Finish working with the wizard](ndmp_server_summary.md).

Page updated 2026-07-02


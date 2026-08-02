---
title: "Uninstalling Veeam Components"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_protected_odb_uninstall.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Uninstalling Veeam Components


You can uninstall all Veeam components deployed on an ODB server during protection group setup as a single operation. The following components are removed:

* InterSystems IRIS plug-in
* Veeam Transport service
* Veeam Deployer service

|  |
| --- |
| TIP |
| For details on the components deployed on ODB servers during protection group setup, see [Solution Architecture](iris_hiw.md). |

Before you start the uninstall process, consider the following:

* Veeam Deployer service and Veeam Transport service are not removed from the ODB server if the server is added to the Veeam Backup & Replication infrastructure as a managed server.
* Veeam Deployer service is not removed if Veeam Backup & Replication connects to the ODB server with single-use credentials.
* Prerequisite components installed and used by Veeam products are not removed during the uninstall process. To remove the remaining components, use the built-in tools directly on the ODB server.

To uninstall Veeam components from an ODB server:

1. Open the Inventory view.
2. In the inventory pane, in the Physical and Cloud Infrastructure node, select the InterSystems IRIS protection group that contains the ODB server.
3. In the working area, select the ODB server and click Uninstall everything on the ribbon, or right-click the ODB server and select Uninstall Everything.
4. In the displayed notification window, click Yes.

Page updated 2026-07-29


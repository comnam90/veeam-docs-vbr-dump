---
title: "Step 1. Enable HPE Web Services API Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_enable_web.html"
last_updated: "4/16/2025"
product_version: "13.0.1.1071"
---

# Step 1. Enable HPE Web Services API Server

In this article

Veeam Backup & Replication uses the HPE Web Services API (WSAPI) server to communicate with HPE Alletra Storage MP B10000, 9000, Primera, 3PAR storage systems.

Before you use the WSAPI server, you must make sure that the server is enabled and enable it if needed.

Enabling WSAPI Server Through SSH

To enable the WSAPI server, do the following:

1. Log on to the Processor with administrator privileges:

|  |
| --- |
| #ssh <administrator account>@<SP IP Address> |

1. Run the following command to view the current state of the WSAPI server:

|  |
| --- |
| #showwsapi |

1. If the WSAPI server is not running, run the following command to start it:

|  |
| --- |
| #startwsapi |

1. [For 3PAR StoreServ] Enable the port through which you want to connect to the storage system:

* If the HTTPS port is disabled and you want to enable it, run the following command:

|  |
| --- |
| #setwsapi -https enable |

* If the HTTP port is disabled and you want to enable it, run the following command:

|  |
| --- |
| #setwsapi -http enable |

Enabling WSAPI Server Through Management Console

The following information applies to HPE 3PAR StoreServ and HPE Primera.

To enable the WSAPI server, do the following:

1. In your storage system management console, click 3PAR StoreServ. Select Systems.
2. Select the storage system from the list.
3. In the next window, select Services in the drop-down list.

The state of the WSAPI server is displayed in the WSAPI Provider tab.

If it is not enabled, click the Edit button and enable the server.

Page updated 4/16/2025

Page content applies to build 13.0.1.1071

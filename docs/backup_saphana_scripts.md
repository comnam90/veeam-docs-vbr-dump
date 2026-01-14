---
title: "Database Backup (HDBSQL Scripts)"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_saphana_scripts.html"
last_updated: "9/6/2023"
product_version: "13.0.1.1071"
---

# Database Backup (HDBSQL Scripts)

In this article

After you [configure Veeam Plug-In settings](configure_sap_hana_plugin.md), you can use HDBSQL to back up and restore SAP HANA databases. For details on the HDBSQL backup, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/75a06c444e9a4b3287a46a6a40b4ee69.html?locale=en-US&version=2.0.06).

Prerequisites

Before the backup process, you can use the hdbuserstore tool to set secure storage of SAP HANA connection details.

To configure hdbuserstore, you must log in to SAP HANA HDBSQL as the operating system administrator (<sid>adm) and run the following commands. For details, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/dd95ac9dbb571014a7d7f0234d762fdb.html?locale=en-US&version=2.0.05).

|  |
| --- |
| sh4adm@linux-q0pn:/usr/sap/SH4/HDB01> hdbuserstore SET <key> hostname:30013@SID <username> <password>  sh4adm@linux-q0pn:/usr/sap/SH4/HDB01> hdbsql -U <key> |

Backing Up SAP HANA Databases Using Backint

To back up the database with Backint, use one of the following commands depending on which type of backup you want to perform:

* Full backup of a tenant database.

|  |
| --- |
| backup data for <TENANT\_DATABASE\_NAME> using backint ('backup\_name\_prefix'); |

* Differential backup of a tenant database.

|  |
| --- |
| backup data differential for <TENANT\_DATABASE\_NAME> using backint ('backup\_name\_prefix'); |

* Incremental backup of a tenant database.

|  |
| --- |
| backup data incremental for <TENANT\_DATABASE\_NAME> using backint ('backup\_name\_prefix'); |

* Full backup of a tenant database with the ASYNCHRONOUS option. The ASYNCHRONOUS option can be helpful if you monitor SAP HANA backups on another host and just want to run the backup command from a script. The option runs the backup job in the background and closes the current script session.

|  |
| --- |
| backup data for <TENANT\_DATABASE\_NAME> using backint ('backup\_name\_prefix') ASYNCHRONOUS; |

* Full backup of SYSTEMDB.

|  |
| --- |
| backup data using backint ('backup\_name\_prefix'); |

* Differential backup of SYSTEMDB.

|  |
| --- |
| backup data differential using backint ('backup\_name\_prefix'); |

* Incremental backup of SYSTEMDB.

|  |
| --- |
| backup data incremental using backint ('backup\_name\_prefix'); |

Page updated 9/6/2023

Page content applies to build 13.0.1.1071

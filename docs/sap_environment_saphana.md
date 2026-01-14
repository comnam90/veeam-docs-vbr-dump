---
title: "SAP Environment Planning"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_environment_saphana.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# SAP Environment Planning

In this article

Keep in mind the following requirements and limitations for your SAP environment, before you deploy Veeam Plug-In for SAP HANA.

Scheduling

You can schedule backup operations with all SAP HANA relevant scheduling options like SAP HANA Cockpit (HANA Cockpit 2.0 SPS 06 or later version), SAP DB13 (NW 7.02 SP17 or later version) or external schedulers like cron, UC4, TWS and others. Veeam Plug-In forwards the backups created by SAP HANA integrated backup application to a Veeam backup repository.

To learn how to configure external schedulers, see the [Veeam Plug-In for SAP HANA Best Practices](https://www.veeam.com/blog/optimize-backup-sap-hana-backint.html).

SAP HANA encryption

Veeam Plug-In supports SAP HANA integrated encryption. The encryption processes are performed on the SAP HANA side. Veeam Plug-In is not involved in encryption processing.

Plan the protection of the encryption environment. In case you loose the encryption keys, Veeam Plug-In can only provide an access to the encrypted backup file. To regain full access to the backup files, you will have to decrypt data in your SAP HANA environment. For more information on SAP HANA data encryption, see [this SAP article](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/2.0.03/en-US/8b39eaf4af7a422e9ffd48a62c2558ce.html).

SAP HANA Catalog Backup with Backint

To back up the SAP HANA catalog using Backint, change the settings of the catalog\_backup\_using\_backint parameter in the backup section of the global.ini file. To learn more, see this [SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/ac0804c23d584e2a892ee3c0a67b7e7c.html?version=2.0.03).

SAP HANA Scale-Out Cluster

Consider the following limitations of Veeam Plug-In support for SAP HANA scale-out clusters:

* All backup tasks across the SAP HANA scale-out cluster are performed in parallel.
* On all cluster nodes, Veeam Plug-In must be configured to transfer backups to the same repository.
* Due to the design of SAP HANA databases, the same Veeam Plug-In configuration must be set on all scale-out cluster members, including stand-by nodes.

* Each cluster node must use the same credentials to connect to Veeam servers.

Page updated 11/7/2025

Page content applies to build 13.0.1.1071

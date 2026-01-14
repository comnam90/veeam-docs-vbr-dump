---
title: "System Requirements for Linux on Power"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_saphana_power.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# System Requirements for Linux on Power

In this article

Before you start using Veeam Plug-In for SAP HANA on Linux machines running IBM Power Systems, make sure the following requirements are met.

|  |
| --- |
| Note |
| The following system requirements apply to Veeam Plug-In for SAP HANA for Linux on Power operating in the standalone mode. The managed operation mode is not supported. For details on operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md#modes). |

| Specification | Requirement |
| --- | --- |
| IBM Power | Veeam Plug-In for SAP HANA for Linux on Power supports IBM Power systems with the following processor generations:   * Power9 * Power10 |
| OS | For IBM Power 9, Veeam Plug-In for SAP HANA for Linux on Power supports little endian (LE) versions of the following distributions:   * SLES 15: SP3, SP4, SP5, SP6, SP7 * SLES for SAP Applications 15: SP3, SP4, SP5, SP6, SP7 * SLES 12 SP5 * SLES for SAP Applications 12 SP5 * RHEL 9 for SAP HANA: 9.0, 9.2, 9.4, 9.6 * RHEL 8 for SAP HANA: 8.4, 8.6, 8.8, 8.10 * RHEL 9 for SAP Solutions: 9.0, 9.2, 9.4, 9.6 * RHEL 8 for SAP Solutions: 8.4, 8.6, 8.8, 8.10   For IBM Power 10, Veeam Plug-In for SAP HANA for Linux on Power supports little endian (LE) versions of the following distributions:   * SLES 15: SP3, SP4, SP5, SP6, SP7 * SLES for SAP Applications 15: SP3, SP4, SP5, SP6, SP7 * RHEL 9 for SAP HANA: 9.0, 9.2, 9.4, 9.6 * RHEL 8 for SAP HANA: 8.4, 8.6, 8.8, 8.10  * RHEL 9 for SAP Solutions: 9.0, 9.2, 9.4, 9.6 * RHEL 8 for SAP Solutions: 8.4, 8.6, 8.8, 8.10 |
| SAP HANA Database | Veeam Plug-In for SAP HANA supports SAP HANA 2.0: SPS 02, SPS 03, SPS 04, SPS 05, SPS 06, SPS 07, SPS 08.  Notes:   * Only with Backint version 1.0 is supported. * SAP HANA Express Edition is not supported. * To check whether an OS version is compatible with the SAP HANA release you want to use, see the [SAP HANA Administration Guide](https://launchpad.support.sap.com/#/notes/2235581) (requires an SAP ID). |
| Veeam Backup & Replication | Veeam Backup & Replication 13 supports different on versions of Veeam Plug-In depending on which OS is running on the backup server:   * Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported. * Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.   Keep in mind that if you use an earlier Veeam Plug-In build than the one that is included in the installation ISO file of your Veeam Backup & Replication version, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474). |
| Network | Veeam Plug-In should be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway. |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071

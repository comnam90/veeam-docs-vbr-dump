---
title: "Upgrade Checklist"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/upgrade_vbr_byb.html"
last_updated: "2/23/2026"
product_version: "13.0.1.1071"
---

# Upgrade Checklist


Use the following checklist to ensure your infrastructure is ready for the Veeam Backup & Replication upgrade. The built-in configuration check mechanism of the Veeam Backup & Replication Upgrade wizard performs some of the checks. Still, you can control them manually before starting the upgrade procedure.

Licensing

1. Veeam Backup & Replication 13 uses the same license file format introduced with version 10, so you can use your existing version 10, 11, or 12 license file to install version 13.
2. Your support contract must be active as of the date when the product build you are installing was built. This is determined by the [support expiration date](license_grace.md) in the installed license. If required, you can install a new license during the upgrade procedure.

System Requirements

1. Verify that the backup server to be upgraded is running a supported operating system as specified in [System Requirements](system_requirements.md#backup_server_windows). If not, perform a configuration backup, install Veeam Backup & Replication 13.0.1 (build 13.0.1.180) on a supported OS, and restore the configuration backup created earlier. For information on how to perform the migration, see [Migrating Veeam Backup & Replication to Another Backup Server](vbr_config_migrate.md).
2. Ensure that the backup server has sufficient disk space. The minimum disk space is calculated dynamically during the system configuration check in the upgrade procedure. It is based on the list of required packages to be installed on the machine and usually is about 9 GB. We recommend allocating at least the minimum disk space calculated during the system configuration check, but not less than 55.5 GB: 3 x ISO size (50.5 GB) in the selected installation path (for example, D:\VBR) plus 5 GB for the database operations on the system volume (for example, C:).
3. Make sure that other servers that you plan to use as backup infrastructure components meet the system requirements listed in [System Requirements](system_requirements.md). In particular, ensure all backup infrastructure servers are based on 64-bit operating systems.
4. Ensure that the environment you are going to protect with Veeam Backup & Replication meets the requirements listed in [Supported Platforms, Applications and Workloads](platform_support.md). In particular:

* Make sure that VMware ESXi and VMware vCenter server are upgraded to the minimum supported version 7.0 or remove these servers from the backup server configuration to continue.
* Make sure that VMware Cloud Director is upgraded to the minimum supported version 10.4 or remove the hosts from the backup server configuration to continue.

1. Backup infrastructure components communicate with each other over specific ports. These ports must be open. For more information, see [Ports](used_ports.md).

|  |
| --- |
| Important |
| Ensure that port 443 is open and available on your backup server, as it is required for Veeam Backup & Replication Web UI operations. If port 443 is unavailable, the upgrade process will be blocked and will not proceed. |

1. Make sure that all necessary permissions are granted. For information on permissions, see [Permissions for VMware vSphere](https://helpcenter.veeam.com/docs/vbr/permissions/cumulativepermissions.html?ver=13).
2. Review the list of required [Trusted Root Certificates](trusted_root_certificates.md), and ensure all are installed.
3. Do you have legacy per-machine backup format with single metadata file? Detach or upgrade such backups to a new format to proceed with the upgrade.
4. Do you have legacy backup copy jobs? Switch your existing backup copy jobs to a supported mode before upgrading.
5. Do you have nested repository paths? Configurations where one repository is located inside another are no longer supported.
6. Do you use UNC path in export vbk wizard? Configurations with such settings are no longer supported.
7. Do you have file copy jobs? The backup server can no longer be used as a destination for File Copy jobs. Update the configuration for these jobs before proceeding with the upgrade.
8. Do you have Veeam Hardened Repository v2 added to the backup infrastructure? Consider upgrading Veeam Hardened Repository to the latest version using Veeam Infrastructure Appliance.
9. Do you have the FIPS mode option enabled? Persistent components will be required for guest processing.
10. Do you have trusted hosts hardening set to Manual? After the upgrade, open the backup console and make sure all your backup infrastructure servers are trusted.
11. Do you have any jobs using the Transform previous backup chains into rollbacks option? This option has been removed from the product, and such jobs are no longer supported.
12. The following features are no longer available in the product.

Deprecated features:

* Restore point–based retention is no longer available for newly created jobs.
* Reversed incremental backup mode is no longer available for newly created jobs.
* Single-storage backup format option is no longer available in the repository settings.
* Active Directory–based authentication is no longer available for new Veeam Cloud Connect tenants.

Discontinued features:

* Universal Application-Item Recovery wizard (U-AIR).
* Initiating restore by double-clicking VBK/VBM files in Windows Explorer.
* Burning Recovery Media to a CD/DVD/BD media.

1. Are you using installations of Veeam Backup & Replication and Veeam Backup for Microsoft 365 on the same machine? First upgrade Veeam Backup for Microsoft 365, second upgrade Veeam Backup & Replication.
2. Are you using Server 2019-based ReFS backup repositories? If yes, avoid upgrading them to Server 2022 or mounting ReFS volumes from Server 2019 to new Server 2022 installations until you read [this thread](https://forums.veeam.com/veeam-backup-replication-f2/windows-server-2022-refs-megathread-t76458.html) on Veeam R&D forums. Microsoft has addressed the known regression in the ReFS format upgrade code, and the fix is now publicly available.
3. Are you using Scale-Out Backup Repositories with immutable performance tier extents? Make sure that all extents have the same immutability settings.
4. Are you using a customized AntivirusInfos.xml file? During the upgrade, Veeam Backup & Replication will replace it with the default file. Make sure that you save your customized file at another path and make necessary changes to the default file after the upgrade.
5. Azure compute accounts based on Azure AD user credentials (created with the Use the existing account option) are obsolete. Replace these accounts with new ones to restore workloads to Microsoft Azure, use the Microsoft Azure archive storage or Microsoft Azure Plug-In for Veeam Backup & Replication appliance.
6. Are you using integration with Veeam Backup for Microsoft Azure? If yes, after upgrading to Veeam Backup & Replication 13 and replacing the obsolete accounts from p.22, select the existing Microsoft Azure compute account in Manage Cloud Credentials, click Edit, and go through the [Microsoft Azure Compute Account](restore_azure_accounts.md) wizard to update account permissions. Otherwise, you can face problems when adding an external repository with backups created by Veeam Backup for Microsoft Azure.

Integration with Veeam Management and Monitoring Products

1. Are you using Veeam ONE to monitor your backup infrastructure? If yes, upgrade it first. Veeam ONE 13 supports monitoring of backup servers version 12 or later.
2. Are you using Veeam Backup Enterprise Manager? If yes, start the upgrade procedure with this component. Veeam Backup & Replication should be upgraded after that. If you have a backup server installed on the same machine, upgrade it immediately after completing upgrade of the Veeam Backup Enterprise Manager server without restarting the machine. Otherwise, the [Veeam Configuration Database Connection Utility](dbconfig_utility.md) (DBConfig) utility will not work correctly for Veeam Backup & Replication.
3. Are you using Veeam Backup Enterprise Manager server added to Veeam ONE? If yes, first upgrade Veeam ONE, second upgrade Veeam Backup Enterprise Manager, and third upgrade Veeam Backup & Replication.
4. Are you using Veeam Cloud Connect? If yes, consider the following:

* Check with your Cloud Connect service provider if they have already upgraded their system to at least the version you are upgrading to.
* Ensure your Cloud Connect tenants use the supported Veeam product versions. The minimal supported tenant versions are: Veeam Backup & Replication 12.3.2.3617, Veeam Agent for Microsoft Windows 6.3.2, Veeam Agent for Linux 6.3.2, Veeam Agent for Mac 2.3.1.
* The Veeam Cloud Connect Portal functionality is deprecated and cannot be used anymore.

Integration with Veeam Backup for Public Clouds

Are you using Veeam Backup & Replication integrated with Veeam Backup for Public Cloud solutions? If yes, first upgrade Veeam Backup & Replication to version 13.0.1 (build 13.0.1.180). Second upgrade plug-ins for Veeam Backup for AWS, Veeam Backup for Microsoft Azure and Veeam Backup for Google Cloud. Third upgrade connected appliances to the most recent version.

Integration with Veeam Virtualization Plug-Ins

Are you using Veeam Backup & Replication integrated with Veeam Virtualization Plug-Ins?

* Veeam Plug-In for Nutanix AHV: During the upgrade to version 13.0.1, the plug-in for this product will be automatically upgraded to the required version. For details, see [Upgrading to Veeam Plug-in for Nutanix AHV 9](https://helpcenter.veeam.com/docs/vbahv/userguide/upgrading_vbahv.html?ver=9) in the Veeam Plug-In for Nutanix AHV User Guide.
* Veeam Plug-in for Oracle Linux Virtualization Manager and Red Hat Virtualization: During the upgrade to version 13.0.1, the plug-in for this product will be automatically upgraded to the required version. For details, see [Upgrading to Veeam Plug-in for OLVM and RHV 7](https://helpcenter.veeam.com/docs/vbrhv/userguide/upgrading.html?ver=7) in the Veeam Plug-in for Oracle Linux Virtualization Manager and Red Hat Virtualization User Guide.
* Veeam Plug-In for Proxmox Virtual Environment: During the upgrade to version 13.0.1, the plug-in for this product will be automatically upgraded to the required version. For details, see [Upgrading to Veeam Plug-in for Proxmox VE 3](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/upgrading.html?ver=3) in the Veeam Plug-In for Proxmox VE User Guide.

Integration with Veeam Backup Agents and Enterprise Plug-Ins

1. Are you using Veeam Agents managed through Veeam Backup & Replication?

* If you use Veeam Agent for Microsoft Windows or Veeam Agent for Linux below 6.3.1, they will stop working after upgrading to Veeam Backup & Replication 13. In this case, we recommend immediately upgrading Veeam Agent for Microsoft Windows or Veeam Agent for Linux to 13. If you use Veeam Agent for Microsoft Windows or Veeam Agent for Linux 6.3.1 or later, they will continue working after upgrading to Veeam Backup & Replication 13, but new features implemented in Veeam Backup & Replication 13 will not be supported. In this case, you can upgrade Veeam Agent for Microsoft Windows or Veeam Agent for Linux to 13 later if the support of new features is not critical for you.
* If you use Veeam Agent for Mac below 2.3.1, it will stop working after upgrading to Veeam Backup & Replication 13. In this case, we recommend immediately upgrading Veeam Agent for Mac to 13. If you use Veeam Agent for Mac 2.3.1 or later, it will continue working after upgrading to Veeam Backup & Replication 13, but new features implemented in Veeam Backup & Replication 13 will not be supported. In this case, you can upgrade Veeam Agent for Mac to 13 later if the support of new features is not critical for you.

1. Are you using Veeam Plug-In for Oracle RMAN, Veeam Plug-In for SAP HANA, Veeam Plug-In for SAP on Oracle, Veeam Plug-In for IBM Db2 or Veeam Plug-In for Microsoft SQL Server? If yes, upgrade Veeam Backup & Replication first, then you can upgrade Veeam Plug-Ins ([Veeam Plug-In for Oracle RMAN](update_rman_plugin.md), [Veeam Plug-In for SAP HANA](update_saphana_plugin.md), [Veeam Plug-In for SAP on Oracle](update_sap_on_oracle_plugin.md), [Veeam Plug-In for IBM Db2](db2_upgrade.md), [Veeam Plug-In for Microsoft SQL Server](update_mssql_plugin.md)).

Integration with Storage Systems

1. IBM FlashSystem: If you are using IBM FlashSystem Plug-In for Veeam Backup & Replication, upgrade it to version 2.3.77 or later. If the plug-in version is lower than the minimum required, storage integration will not function.
2. Hitachi VSP: If you are using Hitachi for Veeam Backup & Replication, upgrade it to version 2.2.271 or later. If the plug-in version is lower than the minimum required, storage integration will not function. Note that the integration with Hitachi is available starting from Veeam Backup & Replication version 13.0.1.1071.
3. HPE XP: If you are using HPE XP Plug-In for Veeam Backup & Replication, storage integration will stop working after the upgrade. Plug-in version with support for Veeam Backup & Replication will be released by the vendor later.
4. NEC Storage V Series: If you are using NEC Storage V Series Plug-In for Veeam Backup & Replication, storage integration will stop working after the upgrade. Plug-in version with support for Veeam Backup & Replication will be released by the vendor later.
5. Make sure your storage systems work on a supported operating system:

* Cisco HyperFlex: The minimum supported operating system version is v5.0 (2x). Upgrade to it or remove the storage arrays from the backup server configuration. Also note that support for Cisco HyperFlex in this release is experimental.
* HPE Nimble: The minimum supported operating system version is 5.2. Upgrade to it or remove the storage arrays from the backup server configuration.
* Dell Data Domain: The supported operating system version is 7.9 to 8.3. Upgrade to it, or the backup jobs pointed to this repository will fail to start.
* ExaGrid: The minimum supported operating system version is 7.2.0 P08. Upgrade the storage array and Veeam Backup & Replication, open the corresponding Linux host properties and complete the wizard to install persistent data mover components on the storage array. If the same array was added twice under different names in the previous version, complete the wizard for one of the hosts and re-point all backup repositories to it.
* Fujitsu CS800: The minimum supported operating system version is 5.2.0. Upgrade the storage array and Veeam Backup & Replication, open the corresponding Linux host properties and complete the wizard to install persistent data mover components on the storage array. If the same array was added twice under different names in the previous version, complete the wizard for one of the hosts and re-point all backup repositories to it.
* Infinidat InfiniGuard: The minimum supported operating system version is 5.2.0. Upgrade the storage array and Veeam Backup & Replication, open the corresponding Linux host properties and complete the wizard to install persistent data mover components on the storage array. If the same array was added twice under different names in the previous version, complete the wizard for one of the hosts and re-point all backup repositories to it.
* Quantum DXi: The minimum supported operating system version is 5.2.0. Upgrade the storage array and Veeam Backup & Replication, open the corresponding Linux host properties and complete the wizard to install persistent data mover components on the storage array. If the same array was added twice under different names in the previous version, complete the wizard for one of the hosts and re-point all backup repositories to it.

Upgrade Process

1. Make sure the latest run for all existing jobs has completed successfully. Rerun any failed jobs.
2. Ensure there are no running jobs, restore sessions, Instant Recovery sessions, and SureBackup jobs. We recommend that you do not stop running jobs and let them complete successfully.
3. Disable any periodic and backup copy jobs temporarily to prevent them from starting during the upgrade.
4. Disable CDP policies. Otherwise the CDP filter will not be upgraded.
5. Ensure there are no active tasks from standalone (unmounted) agents.
6. Ensure there are no active Veeam Recovery Orchestrator tasks.
7. Perform the configuration backup, as described in [Running Configuration Backups Manually](vbr_config_manually.md).
8. Ensure you have configuration backup encryption enabled, otherwise stored credentials will not be included in it. For more information, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md).



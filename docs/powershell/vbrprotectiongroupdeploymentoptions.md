---
title: "VBRProtectionGroupDeploymentOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrprotectiongroupdeploymentoptions.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRProtectionGroupDeploymentOptions


Contains Veeam Agent deployment settings for a protection group.

Properties

| Property | Type | Description |
| --- | --- | --- |
| DistributionServer | CHost | The distribution server responsible for Veeam Agent setup files delivery to computers added to the protection group. |
| InstallAgent | bool | Indicates if Veeam Backup & Replication automatically installs Veeam Agents on all discovered computers of the protection group. |
| UpgradeAutomatically | bool | Indicates if Veeam Backup & Replication automatically upgrades Veeam Agents on discovered computers when the new Veeam Agent version or private fix appears on the distribution server. |
| InstallDriver | bool | Indicates if Veeam Backup & Replication automatically installs the CBT driver on discovered computers protected with Veeam Agent for Microsoft Windows. |
| RebootIfRequired | bool | Indicates if Veeam Backup & Replication reboots discovered computers after the CBT driver installation. |

Related Commands

[New-VBRProtectionGroupDeploymentOptions](new-vbrprotectiongroupdeploymentoptions.md)



---
title: "Licensing"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_licensing.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Licensing


Veeam Backup for Microsoft Entra ID is licensed by the number of protected Microsoft Entra ID users. Each 10 protected users consume one Veeam Universal License instance from the license scope. All Enabled Member users in the organization must be licensed, partial user coverage is not allowed by Microsoft Entra ID.

For the license consumption, Veeam Backup for Microsoft Entra ID counts only enabled member users. The tenant to whom these users belong must have a restore point created during the past 31 days. Note that disabled users, guest users and logs do not consume license instances, but Veeam Backup for Microsoft Entra ID still protects them.

By default, Veeam Backup for Microsoft Entra ID automatically revokes a license instance from protected users if no new restore points have been created during the past 31 days. However, you can manually revoke license instances from protected users as described in the Veeam Backup & Replication User Guide, section [Revoking License](https://helpcenter.veeam.com/docs/vbr/userguide/revoke_servers.html?ver=13).

Obtaining New License

Tenant Backup

Backing up of Microsoft Entra ID tenants is available for all types of licenses:

* No license (Community Edition, free) is when you do not have the license key. With the Community Edition, you get 10 instances that allow protection of 100 enabled member users.

For more information, see [Veeam Backup & Replication Community Edition](https://www.veeam.com/virtual-machine-backup-solution-free.html).

* Evaluation license (free) is a license that can be used for product evaluation. The license is valid for 30 days from the moment of the product download.

To obtain this license, request a trial key on the [Veeam downloads page](https://www.veeam.com/kvm-backup-recovery-download.html) as described in  in the Veeam Backup & Replication User Guide, section [Obtaining and Renewing License](https://helpcenter.veeam.com/docs/vbr/userguide/license_obtain.html?ver=13).

* NFR license (free) is a license used for product demonstration, training and education. The person to whom the license is provided agrees that the license is not for resell or commercial use.

* Subscription license (paid) is a license with a limited subscription term. The expiration date of the Subscription license is set to the end of the subscription term. The Subscription license term is normally 1–3 years from the license issue date.

To obtain this license, choose the required subscription term on the [Veeam Backup & Replication Pricing](https://www.veeam.com/buy-veeam-backup-replication.html) page and contact the Veeam Sales Team.

* Perpetual license (paid) is a license without an expiration date. The Perpetual license typically includes one year period of basic support and maintenance that can be extended.

To obtain this license, [contact a reseller in your region](https://www.veeam.com/buy-veeam-products-pricing.html).

* Rental license (paid) is a license with the license expiration date set according to the chosen rental program (normally 1-12 months from the date of license issue). The Rental license can be automatically updated upon expiration.

Rental licenses are provided to Veeam Cloud & Service Providers (VCSPs) only. For more information, see the [Rental License](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_hosting_licenses.html?ver=120) section in the Veeam Cloud Connect Guide.

|  |
| --- |
| Note |
| Protection of Conditional Access policies is included in the Veeam Data Platform Advanced or Premium. For more details about all Veeam Data Platform packages, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf). |

After you obtain a license, install it on the backup server as described in the Veeam Backup & Replication User Guide, section [Installing License](https://helpcenter.veeam.com/docs/vbr/userguide/install_license.html?ver=13).

Log Backup

The feature is included in the Veeam Data Platform Advanced or Premium. For more details about all Veeam Data Platform packages, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).

Using Existing License

If you already use Veeam Backup & Replication and you have spare Veeam Universal License instances on your backup server, they can be used to protect Microsoft Entra ID tenants. You can check the number of available license instances in the Veeam Backup & Replication console as described in the [Viewing License Information](https://helpcenter.veeam.com/docs/vbr/userguide/license_view.html?ver=13) section in the Veeam Backup & Replication User Guide.

If you have a legacy perpetual per-socket license, you must obtain Veeam Universal License instances and merge them with the existing perpetual socket license as described in the Veeam Backup & Replication User Guide, section [Merging Licenses](https://helpcenter.veeam.com/docs/vbr/userguide/license_merge.html?ver=13) section.



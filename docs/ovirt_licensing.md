---
title: "Licensing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_licensing.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Licensing


Each protected VM consumes one Veeam Universal License instance from the license scope. A VM is considered protected if it has a restore point created during the past 31 days.

By default, Veeam Backup & Replication automatically revokes a license instance from a protected VM if no new restore points have been created during the past 31 days. However, you can manually revoke license instances from protected VMs as described in section [Revoking License](revoke_servers.md).

Obtaining New License

You can obtain the following types of licenses for Veeam Plug-in for Proxmox VE:

* Evaluation license is a free license that can be used for product evaluation. The license is valid for 30 days from the moment of the product download.

To obtain this license, request a trial key on the [Veeam downloads page](https://www.veeam.com/kvm-backup-recovery-download.html) as described in section [Obtaining and Renewing License](license_obtain.md).

* Subscription license is a paid license with a limited subscription term. The expiration date of the Subscription license is set to the end of the subscription term. The Subscription license term is normally 1–5 years from the license issue date.

To obtain this license, choose the required subscription term on the [Veeam Backup & Replication Pricing](https://www.veeam.com/buy-veeam-backup-replication.html) page and contact the Veeam Sales Team.

* Perpetual license is a paid license without an expiration date. The Perpetual license typically includes one year period of basic support and maintenance that can be extended.

To obtain this license, [contact a reseller in your region](https://www.veeam.com/buy-veeam-products-pricing.html).

After you obtain a license, install it on the backup server as described in section [Installing License](install_license.md).

Using Existing License

If you already use Veeam Backup & Replication and you have spare Veeam Universal License instances on your backup server, they can be used to protect Proxmox VE VMs. You can check the number of available license instances in the Veeam Backup & Replication console as described in section [Viewing License Information](license_view.md).



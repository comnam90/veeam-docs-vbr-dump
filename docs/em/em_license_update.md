---
title: "Updating License"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_license_update.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Updating License


To be able to use all data protection and disaster recovery features, you must update your license upon expiry.

You can use the following methods to update the license:

* [Updating license manually](#UpdatingLicenseManually)
* [Updating license automatically](#UpdatingLicenseAutomatically)

|  |
| --- |
| Note |
| When updating the license, Veeam Backup Enterprise Manager requires internet access to connect to the Veeam License Update Server. If your network is not connected to the internet, you can download a new license file from [my.veeam.com](https://my.veeam.com) and install a new license. For more information on license installation, see [Installing License](em_license_install.md). |

Updating License Manually

You can update the license manually on demand. When you update the license manually, Veeam Backup Enterprise Manager connects to the Veeam License Update Server, downloads a new license from it (if the license is available) and installs it.

To update the license, take the following steps:

1. Sign in to Veeam Backup Enterprise Manager using an account with the Portal Administrator role.
2. To open the Configuration view, click Configuration in the upper-right corner.
3. In the Configuration view, open the Licensing section.
4. On the Summary tab, click Details.
5. Click the Update now link.

![Updating License](images/em_lic_per_vm_95.webp "Updating License")

Updating License Automatically

You can instruct Veeam Backup Enterprise Manager to schedule automatic connection with Veeam License Update Server and periodically send requests for a new license. When the automatic update is enabled, Enterprise Manager requests a new license weekly, and 7 days before current license expiration date — daily.

To enable automatic update, do the following:

1. Sign in to Veeam Backup Enterprise Manager using an account with the Portal Administrator role.
2. To open the Configuration view, click Configuration in the upper-right corner.
3. In the Configuration view, open the Licensing section.
4. On the Summary tab, click Details.
5. In the Details window, select the Update license key automatically check box. If this option is enabled in Enterprise Manager (even if it is disabled in the Veeam Backup & Replication console), automatic update will be performed anyway and Enterprise Manager will obtain a new key from Veeam licensing server and propagate it to all managed Veeam backup servers.
6. To receive proactive technical support services, select the Receive proactive support check box. Selecting this option also enables diagnostic data sharing. To learn how sensitive data is processed, see [Processing of Sensitive Data in Veeam Technical Support](https://www.veeam.com/processing_of_sensitive_data_in_support_ds.pdf).

|  |
| --- |
| Note |
| For information on license management in Veeam Backup & Replication, see the [Licensing](https://helpcenter.veeam.com/docs/vbr/userguide/licensing.html?ver=13) section of the Veeam Backup & Replication User Guide.  For information on license management for Veeam Cloud Connect Server Providers, see the [Licensing for Service Providers](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_licensing.html?ver=13) section of the Veeam Cloud Connect Guide. |

Grace Period

Veeam Backup Enterprise Manager supports a grace period after the license expiration date. For Subscription license, it lasts for 30 days, for Rental license — 2 months. During this period the product will be running, but a warning about license expiration (grace period) will appear on the Dashboard tab and in the sessions information. You must update your license before the end of the grace period.

Messages that appear in the automatic license update session log are listed in the [License Update Session Data](license_update_session_data.md) section. Similar messages are received as pop-ups after you force the immediate update.



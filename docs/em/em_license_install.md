---
title: "Installing License"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_license_install.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---

# Installing License


When you first log in to Veeam Backup Enterprise Manager after the deployment, you must install a license. The license will be automatically applied to all backup servers added to Enterprise Manager. This approach simplifies tracking license usage and license updates across multiple backup servers.

|  |
| --- |
| Note |
| * Enterprise Manager on Linux is supported only with the Enterprise Plus edition license. * If a backup server running an earlier version uses a different license type than Enterprise Manager, the backup server existing license will remain unchanged and the Enterprise Manager license will not be applied to the backup server. However, all workloads protected by the backup server will still be count toward the Enterprise Manager license. |

To install a license, take the following steps:

1. Sign in to Veeam Backup Enterprise Manager using an account with the Portal Administrator role.
2. To open the Configuration view, click Configuration in the upper-right corner.
3. In the Configuration view, open the Licensing section.
4. On the Summary tab, click Install license.
5. Select the necessary LIC file and click Open.

[![Installing License](images/license_summary.webp)](images/license_summary.webp "Installing License")



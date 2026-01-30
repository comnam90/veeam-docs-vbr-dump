---
title: "Step 7. Review Server Time Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_linux_iso_install_time.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Step 7. Review Server Time Settings


At the Time step of the Initial Configuration wizard, review server time configuration. Server time affects multi-factor authentication and backup operations, for example, backup job schedule.

Configure the following server time settings:

* Time zone. By default, UTC is used. To specify another time zone, select Change.
* Available NTP servers. By default, the time.nist.gov NTP server is used. You can add multiple NTP and NTS servers. It is recommended to use a minimum of 3 to mitigate timing issues.

|  |
| --- |
| Note |
| NTS servers must use a certificate signed by a public certificate authority. |

To synchronize time on the backup server with the NTP servers, select Sync.

You can change server time settings later in the Host Management console. For more information, see [Configuring Server Time Settings](hmc_configure_time.md).

![Step 7. Review Server Time Settings](images/deployment_iso_install_time.webp)



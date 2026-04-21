---
title: "Starting SureBackup Job in Troubleshooting Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_job_troubleshooting_hv.html"
last_updated: "4/20/2026"
product_version: "13.0.1.2067"
---

# Starting SureBackup Job in Troubleshooting Mode


If a VM fails to be verified, you can start it in the troubleshooting mode to investigate the issue. This can be helpful for diagnosing internal connectivity issues in the lab and inspecting the appropriate values for [Maximum allowed boot time and Application initialization timeout](surebackup_job_tests_hv.md#startup).

|  |
| --- |
| Note |
| Consider the following:   * Troubleshooting mode will force the selected VM and the application group to remain powered on until you manually stop the session. * If the application group has already been powered off when troubleshooting mode is initiated, it will be powered on again. * Troubleshooting mode can be initiated while the SureBackup job is still running or after it completes. * If troubleshooting mode is initiated while the job is running, the SureBackup job will first process all other VMs, then enter troubleshooting mode for the selected VM. |

To start a VM in troubleshooting mode:

1. Open the Home view.
2. In the inventory pane, select SureBackup under Jobs.
3. In the working area, right-click the SureBackup job and select Statistics. You can also double-click the job in the list.
4. Right-click the failed VM and select Start.

To stop the troubleshooting mode session, do one of the following:

* In the Session Statistics window, right-click the VM and select Stop.
* In the working area, select the SureBackup job and click Stop on the ribbon. You can also right-click the SureBackup job and select Stop.



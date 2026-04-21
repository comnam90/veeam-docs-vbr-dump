---
title: "Viewing Recovery Verification Job Statistics"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/viewing_surebackup_stats.html"
last_updated: "4/20/2026"
product_version: "13.0.1.2067"
---

# Viewing Recovery Verification Job Statistics


You can monitor how tests for verified VMs are performed while a recovery verification job is running.

To see the status of VM tests:

1. Open the Home view.
2. In the inventory pane, select SureBackup under Jobs.
3. In the working area, right-click a recovery verification job and select Statistics. You can also double-click the job in the list.

The job session window displays statistics for all VMs that are started during the SureBackup job: VMs from the application group in the specified order and VMs from linked jobs. For your convenience, these VMs are marked with different icons.

After the verified VM is powered on, its name is displayed as a hyperlink. You can click the link to open the VM console to see what is happening inside the VM or perform manual testing.

If some VM fails to be verified automatically, you can start it in the troubleshooting mode. For more information, see [Starting SureBackup Job in Troubleshooting Mode](surebackup_job_troubleshooting.md).

If you enabled content analysis at the [Settings step](surebackup_job_settings_vm.md) of the SureBackup job wizard, you can view the detailed logging of the scan process. To view logs, click the Scan Log button that will appear at the bottom of the job session window after the scan is complete.

![Viewing Recovery Verification Job Statistics](images/surebackup_stats_vm.webp)



---
title: "Step 8. Verify Instant Recovery Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_verify_vm_web.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Step 8. Verify Instant Recovery Settings


At the Summary step of the wizard, specify additional settings for Instant Recovery:

1. If you recover failed production workloads and want to recover them with initial network settings, select the Connect VM to network check box.

If you recover workloads for testing disaster recovery while the original workloads are still running, leave this check box unselected. Before you power on the recovered VMs, you must disconnect them from the production network and connect to a non-production network to avoid conflicts.

1. To start the recovered VMs right after recovery, select the Power on target VM after restoring check box. If you recover the VMs to the production network, make sure that the original workloads are powered off.
2. Check the settings that you have specified for Instant Recovery and click Finish.

[![Finalize Recovery - Web UI](images/instant_recovery_verify_vm_web.webp)](images/instant_recovery_verify_vm_web.webp "Finalize Recovery - Web UI")

What You Do Next

[Finalizing Instant Recovery to VMware vSphere](instant_recovery_review_vm_web.md)



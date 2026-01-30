---
title: "Step 8. Schedule Switch to Production vApps"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_failback_schedule.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Step 8. Schedule Switch to Production vApps


At the Failback Mode step of the wizard, specify when switch from replicas to production vApps must be performed:

* Select Auto if you want Veeam Backup & Replication to perform the switch automatically right after the state of the production vApps is synchronized with the state of their replicas.
* Select Scheduled if you want Veeam Backup & Replication to perform the switch at a specific time.
* Select Manual if you want to perform the switch manually.

If you select the Scheduled or Manual option, you can further reset or set the scheduled time or switch to the production VM manually. For more information, see [Changing Switching Time](vcd_cdp_failback_switching_time.md) and [Switching to Production vApps Manually](vcd_cdp_failback_switch.md).

![Step 8. Schedule Switch to Production vApps](images/vcd_failback_switch_shedule.webp)



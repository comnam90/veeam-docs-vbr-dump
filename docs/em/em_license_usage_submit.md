---
title: "Submitting Monthly Usage Report"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_license_usage_submit.html"
last_updated: "1/14/2026"
product_version: "13.0.1.1071"
---


In this article

On the first day of the month, Veeam Backup Enterprise Manager shows a warning on the Dashboard tab. The warning prompts you to submit a monthly usage report and informs you on the number of days within which the report must be submitted.

Depending on whether [automatic license updating](em_license_update) is enabled or disabled, you can submit a monthly usage report from [Veeam Backup Enterprise Manager](#em) or the [VCSP Pulse Portal](#pulse).

For more information about how license usage reporting works, see the [License Usage Reporting](https://helpcenter.veeam.com/docs/vbr/cloud/sp_license_usage_report.html?ver=13) section of the Veeam Cloud Connect Guide.

Submitting Report from Veeam Backup Enterprise Manager

If [automatic license update](em_license_update.md) is enabled, you can send the monthly usage report directly from Veeam Backup Enterprise Manager. If you do not submit the report within 3 days, Veeam Backup Enterprise Manager sends the report automatically.

To submit a monthly usage report before the automatic submission, perform the following steps:

1. In the monthly usage report notification, click the submit link.
2. In the Monthly Usage Report window, to check or change the number of used instances, click Review.

For more information, see [Reviewing Monthly Usage Report](em_license_usage_review.md) and [Adjusting Monthly Usage Report](em_license_usage_adjust.md).

1. To submit the report, click Send.

You can also postpone the report submission. To do this, click Postpone. In this case, Veeam Backup Enterprise Manager closes the Monthly Usage Report window. Until the report is sent to Veeam, on the Dashboard tab, Enterprise Manager keeps displaying a warning prompting to submit the report.

[![Submitting Monthly Usage Report Automatically](images/license_report_notification.webp)](images/license_report_notification.webp "Submitting Monthly Usage Report Automatically")

Submitting Report from VCSP Pulse Portal

If [automatic license update](em_license_update.md) is disabled, you must manually fill out and send the report in the VCSP Pulse Portal before the day defined by the agreement with Veeam or your Veeam Aggregator (if any is involved). The default day is the sixth day of the month.

To submit a monthly usage report from the VCSP Pulse Portal, perform the following steps:

1. In the monthly usage report notification, click the submit link.
2. In the Monthly Usage Report window, to check or change the number of used instances, click Review. For more information, see [Reviewing Monthly Usage Report](em_license_usage_review.md) and [Adjusting Monthly Usage Report](em_license_usage_adjust.md).
3. To download the report, click Download.

You can also postpone the report submission. To do this, click Postpone. In this case, Veeam Backup Enterprise Manager closes the Monthly Usage Report window. Until the report is sent to Veeam, on the Dashboard tab, Enterprise Manager keeps displaying a warning prompting to submit the report.

1. Fill out the report in the VCSP Pulse Portal with the used workloads and licenses and submit it, as described in the [Using VCSP Pulse](https://helpcenter.veeam.com/docs/vcsp/refguide/using_vcsp_pulse.html#submitting-license-usage) section of the Veeam Rental Licensing and Usage Reporting Reference Guide.

Page updated 1/14/2026

Page content applies to build 13.0.1.1071

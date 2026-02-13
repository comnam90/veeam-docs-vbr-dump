---
title: "Publishing Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_pit_state.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Publishing Point-in-Time State


Publishing a point-in-time state allows you to load the required database state and unroll specified transactions if needed.

To publish a standalone database or a Data Guard database as of a point-in-time state, do the following:

1. [Launch the Publish wizard](veor_lpw.md).
2. [Specify a restore point](veor_srp.md).
3. [Fine-tune the restore point](veor_finetune.md).
4. [Review the publishing summary](veor_publish_pit_summary.md).

|  |
| --- |
| Note |
| Point-in-time restore is available only if archived log backups exist. For more information, see [Required Job Settings](veo_bu_job_settings.md). |



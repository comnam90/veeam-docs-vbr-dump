---
title: "Viewing SLA-Based Backup Policy Details"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sla_policy_view.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Viewing SLA-Based Backup Policy Details


After you create an SLA-based backup policy, the backup appliance displays this policy on the SLA-Based tab of the Policies page. Each policy is described with the following set of properties:

* Priority — the priority of the policy.
* Policy — the name of the policy.
* Description — the reference information on the policy.
* Snapshot SLA — the most recent SLA compliance ratio calculated for all snapshots produced by the policy.
* Backup SLA — the most recent SLA compliance ratio calculated for all backups produced by the policy.
* Archive SLA — the most recent SLA compliance ratio calculated for all archived backups produced by the policy.

To see how the SLA compliance ratio has been changing over a specific period (daily, monthly or weekly) for each Azure VM protected by the policy, click the link in the Snapshot SLA, Backup SLA or Archive SLA column. For more information, see [Monitoring SLA-Based Policy Performance](azure_sla_monitoring.md).

[![Viewing SLA-Based Backup Policy Details](images/azure_sla_policy_view.webp)](images/azure_sla_policy_view.webp "Viewing SLA-Based Backup Policy Details")

Page updated 2026-07-01


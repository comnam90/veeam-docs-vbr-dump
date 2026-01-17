---
title: "Viewing Policies"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/reports_on_policies.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Viewing Policies


From Veeam Backup Enterprise Manager, you can view information about all CDP policies from all backup servers added to Enterprise Manager. To view CDP policies, open the Policies tab.

Each policy in the list is described with the following data:

* Name — policy name
* Status — current policy status
* SLA — percentage of sessions completed within the specified RPO
* RPO — recovery point objective, that is, how often to create short-term restore points
* Max delay — difference between the configured RPO and time required to transfer and save data
* Target — target host
* Platform — VMware vSphere or VMware Cloud Director
* Description — policy description

To quickly find a CDP policy, you can use filters and the search field.

* To filter the list of policies:

* Use the Backup server list to view the policies of the selected backup server only.
* Use the Status filter to view the policies with the selected statuses only.

Once you have selected necessary statuses, click the Apply button to apply the filter.

* To find a policy by its name, use the search field.

In addition to the information presented in the list of policies, the Policies tab allows you to view advanced policy data. To see detailed policy statistics, click the state link in the Status column.

|  |
| --- |
| Note |
| You can export displayed information to a file using the Export link on the toolbar. This file then can be opened on the client machine using the associated application. |

[![CDP Policy Statistics](images/em_cdp_policies_tab.webp)](images/em_cdp_policies_tab.webp "CDP Policy Statistics")



---
title: "Mapping Jobs and CDP Policies to Organization Configurations"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_map_jobs_policies.html"
last_updated: "11/22/2024"
product_version: "13.0.1.1071"
---


In this article

Service providers can map backup jobs, replication jobs, and CDP policies created in Veeam Backup & Replication to the organization configurations of their tenants. After you map the jobs and policies, tenants can manage them and perform recovery operations independently in Veeam Self-Service Backup Portal.

|  |
| --- |
| Note |
| Tenants can create their own backup jobs in Veeam Self-Service Backup Portal. However, if a tenant wants to manage replication jobs and CDP policies in the portal, the service provider must create them and map to the tenant organization configuration. |

To map a CDP policy to an organization, take the following steps:

1. In Enterprise Manager, create organization configurations for your tenants. For details, see [Adding Organization Configuration](em_configure_vcd_org.md).
2. In Veeam Backup & Replication, create jobs or CDP policies for your tenants. Ensure that each job (or policy) includes only the objects that belong to a particular Cloud Director organization. Otherwise, you will not be able to map the job.

For backup and replication jobs, you can include any objects from the organization, and your tenant can edit the job later. Editing of CDP policies is not available in Veeam Self-Service Backup Portal.

1. To map the created jobs and policies to the organization configuration, use the [Set-VBRvCloudOrganizationJobMapping](https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcloudorganizationjobmapping.html?ver=13) cmdlet.

You can also use this cmdlet to unmap jobs and policies from an organization configuration.

Page updated 11/22/2024

Page content applies to build 13.0.1.1071

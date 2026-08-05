---
title: "Step 4. Configure Backup Source Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_source_settings_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Configure Backup Source Settings


At the Resources step of the wizard, select AWS Regions where RDS resources that you plan to back up reside, and choose DB instances and Aurora DB clusters to back up.

Step 4a. Select AWS Regions

In the Regions section of the Resources step of the wizard, choose AWS Regions where RDS resources that you plan to back up reside:

1. Click Choose regions.
2. In the Choose regions window, select the necessary regions from the Available Regions list, and then click Add.

The list of available regions will depend on the option you selected at [step 3](aws_add_policy_scope_rds.md) of the wizard. If you have selected the Organization option, the list will contain all existing AWS Regions; if you have selected the Account option, the list will contain all AWS Regions enabled for the AWS account.

1. To save changes made to the backup policy settings, click Apply.

[![Creating RDS Backup Policy](images/aws_rds_backup_source_regions.webp)](images/aws_rds_backup_source_regions.webp "Creating RDS Backup Policy")

Step 4b. Select RDS Resources

In the Resources section of the Resources step of the wizard, specify the backup scope — select DB instances and Aurora DB clusters that the backup appliance will back up:

1. Click Choose resources to protect.
2. In the Choose resources to protect window, choose whether you want to back up all RDS resources from the selected AWS Regions or only specific RDS resources.

If you select the All resources option, the backup appliance will regularly check for new DB instances and Aurora DB clusters launched in the selected regions and automatically update the backup policy settings to include these resources into the backup scope.

If you select the Protect only following resources option, you must also specify the resources explicitly:

1. Use the Type drop-down list to choose whether you want to add individual RDS resources or AWS tags to the backup scope.

If you select the Tag option, the backup appliance will back up only those resources that have specific tags and reside in the selected regions.

1. Use the Database ID drop-down list to find the necessary resource, and then click Protect to add the resource to the backup scope.

For a resource to be displayed in the list of available resources, it must reside in an AWS Region that has ever been specified in any backup policy. Otherwise, the only option to discover the available resources is to click Browse to select specific resources from the global list and to wait for the backup appliance to populate the resource list.

|  |
| --- |
| Tip |
| You can simultaneously add multiple resources to the backup scope. To do that, click Browse to select specific sources from the global list, select check boxes next to the necessary RDS resources or AWS tags in the list of available resources, and then click Protect.  If the list does not show the resources that you want to back up, click Rescan to launch the data collection process. As soon as the process is over, the backup appliance will update the resource list. |

If you add an AWS tag to the backup scope, the backup appliance will regularly check for new RDS resources assigned the added AWS tag and automatically update the backup policy settings to include these resources in the scope. However, this applies only to DB instances and Aurora DB clusters from the AWS Regions selected at [step 4a](#regions) of the wizard. If you select an AWS tag assigned to RDS resources from other AWS Regions, these resources will not be protected by the backup policy. To work around the issue, either go back to step 4a and add the missing AWS Regions, or create a new backup policy.

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| As an alternative to selecting the Protect only following resources option and specifying the resources explicitly, you can select the All resources option and exclude a number of resources from the backup scope. To do that, click Choose resources to exclude and specify the resources or tags that you do not want to protect — the procedure is the same as described for including resources in the backup scope.  Note that if a resource appears both in the list of included and excluded resources, the backup appliance will still not process the resource because the list of excluded resources has a higher priority. |

[![Creating RDS Backup Policy](images/aws_rds_backup_resources.webp)](images/aws_rds_backup_resources.webp "Creating RDS Backup Policy")

Page updated 2026-05-21


Stop-VMs based on priority tag
==============================

            

This runbook stops all of the virtual machines in the specified Azure Resource Group, in order, based on the value of the Priority tag.
It is particularly useful for CSP (Cloud Solution Provider) customers, or users who have multiple subscriptions, as both Tenant ID and Subscription ID can

be specified.

Note: Edit the $CredentialAssetName to match your Automation Credential Asset name.
The account should have VM Contributor rights on the Resource Group you are targeting, or the ability to perform the “stop” VM action.
More info on creating custom RBAC roles can be found here: 
https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/#custom-roles-in-azure-rbac

PARAMETER 
ResourceGroupName
Required
Name of the Azure Resource Group containing the VMs to be stopped.

PARAMETER 
TenantID
Required
Tenant ID of the Azure account you are targeting (use Get-AzureRMSubscription to view). This should be provided in

the format xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx

PARAMETER
SubscriptionID
Required
Subscription ID of the Azure subscription that the Resource Group resides in (use Get-AzureRMSubscription to view).

This should be provided in the format xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx

REQUIREMENTS 
This runbook makes use of the Azure Resource Manager PowerShell global module (now included
in Azure Automation)
Each VM must have a tag called 'Priority' with a value between 1 and 10. The lower number gets turned off last (e.g. 10, 9, 8...2, 1)

NOTES
This runbook was originally created to power off Virtual Machines overnight and at weekends to prevent charging for

resources that are not needed 24x7, it is also ideal for Dev / Test labs. 
The priority tag is useful if there are VMs or appliances which need to be powered off after other resources.


 

 

        
    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.

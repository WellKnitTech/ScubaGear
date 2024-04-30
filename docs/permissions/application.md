# Application Permissions

The Azure AD baseline requires the use of Microsoft Graph. ScubaGear will attempt to configure the required API permissions needed by the Microsoft Graph PowerShell module, if they have not already been configured in the target tenant.

The process to configure the application permissions is sometimes referred to as the "application consent process," because an Administrator must "consent" for the Microsoft Graph PowerShell application to access the tenant and the necessary Graph APIs to extract the configuration data. Depending on the Azure AD roles assigned to the user running the tool and how the application consent settings are configured in the target tenant, the process may vary slightly. To understand the application consent process, read [this article](https://learn.microsoft.com/en-us/azure/active-directory/develop/application-consent-experience) from Microsoft.

Microsoft Graph is used because Azure AD PowerShell is being deprecated.

> **NOTE**: Microsoft Graph PowerShell SDK appears as "unverified" on the AAD application consent screen. This is a [known issue](https://github.com/microsoftgraph/msgraph-sdk-powershell/issues/482).

The following API permissions are required for Microsoft Graph Powershell:

- Directory.Read.All
- GroupMember.Read.All
- Organization.Read.All
- Policy.Read.All
- RoleManagement.Read.Directory
- User.Read.All
- PrivilegedEligibilitySchedule.Read.AzureADGroup
- PrivilegedAccess.Read.AzureADGroup
- RoleManagementPolicy.Read.AzureADGroup

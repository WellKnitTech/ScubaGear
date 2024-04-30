# Service Principal Permissions

The minimum API permissions & user roles for each product that need to be assigned to a service principal are listed in the table below.

TODO:  AAD or ENTRA?

| Product                 | API Permissions                                 | Role          |
| ----------------------- | ----------------------------------------------- | ------------- |
| Azure Active Directory  | Directory.Read.All, GroupMember.Read.All,       |               |
|                         | Organization.Read.All, Policy.Read.All,         |               |
|                         | RoleManagement.Read.Directory, User.Read.All    |               |
|                         | PrivilegedEligibilitySchedule.Read.AzureADGroup |               |
|                         | PrivilegedAccess.Read.AzureADGroup              |               |
|                         | RoleManagementPolicy.Read.AzureADGroup          |               |
| Defender for Office 365 | Exchange.ManageAsApp                            | Global Reader |
| Exchange Online         | Exchange.ManageAsApp                            | Global Reader |
| Power Platform          | (see below)                                     |               |
| SharePoint Online       | Sites.FullControl.All, Directory.Read.All       |               |
| Microsoft Teams         |                                                 | Global Reader |

This [video](https://www.youtube.com/watch?v=GyF8HV_35GA) provides a good tutorial for creating an service principal manually in the Azure console. Augment the API permissions and replace the role assignment instructions in the video with the permissions listed above.

## Power Platform

For Power Platform, the application must be [manually registered to Power Platform via interactive authentication](https://learn.microsoft.com/en-us/power-platform/admin/powershell-create-service-principal#registering-an-admin-management-application) with a administrative account. See [Limitations of Service Principals](https://learn.microsoft.com/en-us/power-platform/admin/powershell-create-service-principal#limitations-of-service-principals) for how applications are treated within Power Platform.

TODO:  Why is there a variable here!!!???

```powershell
# use -Endpoint usgov for gcc tenants
Add-PowerAppsAccount 
  -Endpoint prod 
  -TenantID $tenantId 
# Must be run from a Power Platform Administrator or Global Administrator account
New-PowerAppManagementApp 
  -ApplicationId $appId 
```

TODO: why is this here?  nothing so far has been said about certificates or thumbprints

### Certificate store notes

- Power Platform has a [hardcoded expectation](https://github.com/microsoft/Microsoft365DSC/issues/2781) that the certificate is located in `Cert:\CurrentUser\My`.
- MS Graph has an expectation that the certificate at least be located in one of the local client's certificate store(s).

> **Additional Notes**: Only authentication via `CertificateThumbprint` is currently supported. We will be supporting automated app registration in a later release.
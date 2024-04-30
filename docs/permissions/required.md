# Required Permissions

When executing the tool interactively, there are two types of permissions that are required:

TODO: Should Azure AD be Entra now?

- [User Permissions](user.md) - These are associated with Azure AD roles assigned to a user.
- [Application Permissions](application.md) - These are assigned to the MS Graph PowerShell application in Azure AD.

When executing the tool via app-only authentication, only one type of permission is required:

- [Service Principal Permissions](principal.md) - These are assigned to the service principal.
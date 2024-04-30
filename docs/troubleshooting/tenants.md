# Multiple Tenants

ScubaGear creates connections to several M365 services. If running against multiple tenants, it is necessary to disconnect those sessions.

TODO:  AAD or Entra?

`Invoke-SCuBA` includes the `-DisconnectOnExit` parameter to disconnect each connection upon exit. To disconnect sessions after a run, use `Disconnect-SCuBATenant`. The cmdlet disconnects from Azure Active Directory (via MS Graph API), Defender, Exchange Online, Power Platform, SharePoint Online, and Microsoft Teams.

```powershell
# Disconnect all sessions
Disconnect-SCuBATenant
```

The cmdlet will attempt to disconnect from all services regardless of current session state. Only connections established within the current PowerShell session will be disconnected and removed. Services that are already disconnected will not generate an error.

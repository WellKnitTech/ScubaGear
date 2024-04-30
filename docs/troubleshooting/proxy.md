# Proxy

If you receive connection or network proxy errors, try running:

TODO:  need some explanation of what this does.  And if there's a proxy, where do we configure a proxy for ScubaGear?  Or, similarly, if we are behind ZScaler, where do we add the company/Zscaler certs?

```powershell
$Wcl=New-Object System.Net.WebClient
$Wcl.Proxy.Credentials=[System.Net.CredentialCache]::DefaultNetworkCredentials
```

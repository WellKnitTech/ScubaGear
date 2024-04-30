# Defender

TODO what is the ExchangeOnlineManagement PowerShell Module and what does it have to do with SG?

When running ScubaGear against Defender (via ExchangeOnlineManagement PowerShell Module), you may see a connection error about OAuth in the Powershell window: 

TODO:  Is this error still relevant?  How I can create it to see it?

> WARNING: Please note that you can only use above 9 new EXO cmdlets (the one with *-EXO* naming pattern). You can't use other cmdlets as we couldn't establish a Remote PowerShell session as basic auth is disabled in your client machine. To enable Basic Auth, please check instruction here https://docs.microsoft.com/en-us/powershell/exchange/exchange-online-powershell-v2?view=exchange-ps#prerequisites-for-the-exo-v2-module Create Powershell Session is failed using OAuth.

If you see this error message, it means that you are running a version of the ExchangeOnlineManagement PowerShell module less than Version 3.2. The automation relies on the Microsoft Security & Compliance PowerShell environment for Defender information. Security & Compliance PowerShell connections, unlike other services used by the ExchangeOnlineManagement module, require basic authentication to be enabled. As of June 2023, Microsoft has [deprecated Remote PowerShell for Exchange Online and Security & Compliance PowerShell](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-deprecation-of-remote-powershell-rps-protocol-in/ba-p/3695597). To resolve this error, you should run the `Initialize-SCuBA` cmdlet to install the latest ExchangeOnlineManagement module version.

TODO:  Give an example of running this command or link the page that explains how/when to do this.

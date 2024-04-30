# Exchange Online

When running ScubaGear against Exchange Online, you may see an error about maximum number of connections in the Powershell window:

> New-ExoPSSession : Processing data from remote server outlook.office365.com failed with the following error message: [AuthZRequestId=8feccdea-493c-4c12-85dd-d185232cc0be][FailureCategory=A uthZ-AuthorizationException] Fail to create a runspace because you have exceeded the maximum number of connections allowed : 3

If you see this error message, run the command below in Powershell:

TODO WHy?  What does it do?

```powershell
Disconnect-ExchangeOnline
```

TODO WHy?  What does it do?  And why is this alternately?  Do they do the same thing?
TODO: FIx the bad grammar here.

Alternatively, run `Disconnect-SCuBATenant` exported by the ScubaGear module.

```powershell
Disconnect-SCuBATenant
```

TODO: IS THIS OUT OF DATE BASED UPON WHAT IS DOWNLOADED?

# PowerShell Execution Policies

"PowerShell's [execution policy](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4) is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts. This feature helps prevent the execution of malicious scripts."

On **Windows servers**, the default execution policy is `RemoteSigned`, which allows ScubaGear to run after the publisher (CISA) is agreed to once. ScubaGear is signed by a commonly trusted Certificate Authority (CA). 

TODO:  What does restricted do?  DOES IT PREVENT SG from Running?

On **Windows clients**, the default execution policy is `Restricted`. In this case, the [execution policy can be set](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-5.1) to permit ScubaGear to run.

```powershell
Set-ExecutionPolicy 
  -ExecutionPolicy RemoteSigned 
  WHAT GOES HERE
```

Windows clients with an execution policy of `Unrestricted` generate a warning about running only trusted scripts when executing ScubaGear, even when the scripts and modules are signed, because the files contain an identifier showing they were downloaded from the Internet. These zone identifiers, informally referred to as [mark of the web restrictions](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4#manage-signed-and-unsigned-scripts), can be removed by running `Unblock-File` on scripts and modules in the ScubaGear folder. 

TODO:  What GOES HERE

```powershell
Unblock-File WHAT GOES HERE
```

Users should use `Unblock-File` carefully and only run it on files they have vetted and deem trustworthy to execute on their system. See Microsoft's documentation on [unblocking files](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1) for more information.
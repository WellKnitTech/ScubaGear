# Utility Scripts

The ScubaGear repository includes several utility scripts in the `utils` folder that can help with troubleshooting and recovering from error conditions. These scripts are designed to assist developers and users when running into errors with the ScubaGear tool or local system environment.

## ScubaGear Support

TODO:  This script is NOT in utils.

If a user receives errors and needs additional support diagnosing issues, the `ScubaGearSupport.ps1` script can be run to gather information about their system environment and previous tool output.
The script gathers this information into a single ZIP formatted archive to allow for easy sharing with developers or other support staff to assist in troubleshooting. Since the script does gather report output, do keep in mind that the resulting archive may contain details about the associated M365 environment and its settings.

The script can be run with no arguments and will only collect environment information for troubleshooting. If the `IncludeReports` parameter is provided, it will contain the most recent report from the default `Reports` folder.

```powershell
.\ScubaGearSupport.ps1
```

An alternate report path can be specified via the `ReportPath` parameter.

```powershell
.\ScubaGearSupport.ps1 -ReportPath C:\ScubaGear\Reports
```

Finally, the script can optionally include all previous reports rather than the most recent one by adding the `AllReports` option.

```powershell
.\ScubaGearSupport.ps1 -AllReports
```

Data gathered by the script includes:

- Listings of locally installed PowerShell modules and their installation paths
- PowerShell versions and environment details
- WinRM client service Basic Authentication registry setting
- (optional) ScubaGear output from one or more previous invocations which contains
  - HTML product and summary reports
  - JSON-formatted M365 product configuration extracts
  - JSON and CSV-formatted M365 baseline test results

## Removing installed modules

ScubaGear requires a number of PowerShell modules to function. A user or developer, however, may wish to remove these PowerShell modules for testing or for cleanup after ScubaGear has been run. The `UninstallModules.ps1` script will remove the latest version of the modules required by ScubaGear and installed by the associated `Initialize-SCuBA` cmdlet. The script does not take any options and can be as follows:

```powershell
# Remove all ScubaGear modules
.\UninstallModules.ps1
```

TODO:  Is PSGet 3.0 still in beta?

PowerShellGet 2.x has a known issue uninstalling modules installed on a OneDrive path that may result in an "Access to the cloud file is denied" error. Installing PSGet 3.0, currently in beta, will allow the script to successfully uninstall such modules; alternatively, the modules can be removed manually from OneDrive.

TODO:  What about this one?

## Deploy UTILS

DeployUtils is in the utils folder.  SHould we talk about it here?
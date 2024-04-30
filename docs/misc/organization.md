# Repository Organization

TODO:  THis is hopelessly out of date.

- `PowerShell` contains the code used to export the configuration settings from the M365 tenant and orchestrate the entire process from export through evaluation to report. The main PowerShell module manifest `ScubaGear.psd1` is located in the `PowerShell/ScubaGear` folder.
- `Rego`, located within the PowerShell/ScubaGear folder, holds the `.rego` files. The Open Policy Agent executable uses each Rego file to audit the desired state for each product, per the SCuBA M365 secure configuration baseline documents.
- `baselines` contains the SCuBA M365 secure configuration baseline documents in Markdown format.
- `Testing` contains code that is used during the development process to test ScubaGear's PowerShell and Rego code.
- `sample-report` contains sample JSON and HTML report output of the ScubaGear tool. Right click on the `BaselineReports.html` to open the file in a browser of your choice to view the sample report.
- `utils` contains an assorted array of helper scripts for ScubaGear usage and development. See [Utility Scripts](#utility-scripts) for detailed descriptions of scripts that can help with troubleshooting.
![CISA Logo](/docs/cisa.png)

<a href="https://github.com/cisagov/ScubaGear/releases" alt="ScubaGear version #">
  <img src="https://img.shields.io/badge/ScubaGear-v1.2.0-%2328B953?labelColor=%23005288" />
</a>
<p>

# ScubaGear

ScubaGear is an assessment tool that verifies that a Microsoft 365 (M365) tenant’s configuration conforms to the policies described in the Secure Cloud Business Applications ([SCuBA](https://cisa.gov/scuba)) Security Configuration Baseline [documents](https://cisagov.github.io/ScubaGear/baselines).

> **NOTE**: This documentation can be read using [GitHub Pages](https://cisagov.github.io/ScubaGear).

## Target Audience

ScubaGear is for M365 administrators who want to assess their tenant environments against CISA's Secure Configuration Baselines.

## Overview

ScubaGear uses a three-step process:

TODO:  Does it really spit out JSON?

* **Step One** - PowerShell code queries Microsoft's M365 APIs for various configuration settings.
* **Step Two** - [Open Policy Agent](https://www.openpolicyagent.org) (OPA) is used to compare these settings against Rego security policies written per  the baseline documents.
* **Step Three** - The results of the comparison are reported as JSON and HTML.

These steps are visualized in an [architecture diagram](docs/images/scuba-architecture.png).

TODO:  THere are a LOT of images in the images folder, but I can't find that anything uses them.  Delete?

## Table of Contents

### Installation

* [Assumptions](docs/installation/assumptions.md)
* [Latest Release](docs/installation/download.md)
* [Execution Policies](docs/installation/powershell.md)

### Usage

* [Module Import](docs/usage/import.md)
* [Execution](docs/usage/execution.md)
* [Parameters](docs/usage/parameters.md)
* [Configuration File](docs/usage/configuration.md)
* [Report](docs/usage/report.md)

### Permissions

- [Required Permissions](docs/permissions/required.md)
- [User Permissions](docs/permissions/user.md)
- [Application Permissions](docs/permissions/application.md)
- [Service Principal Permissions](docs/permissions/principal.md)

### Troubleshooting

- [Multiple Tenants](docs/troubleshooting/tenants.md)
- [Defender](docs/troubleshooting/defender.md)
- [Exchange Online](docs/troubleshooting/exchange.md)
- [Power Platform](docs/troubleshooting/power.md)
- [Microsoft Graph Errors](docs/troubleshooting/graph.md)
- [Proxy](docs/troubleshooting/proxy.md)
- [Utility Scripts](docs/troubleshooting/utilities.md)

### Misc

- [Repository Organization](docs/misc/organization.md)
- [Project License](docs/misc/license.md)

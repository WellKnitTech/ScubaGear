# Configuration File

Most of the `Invoke-SCuBA` cmdlet parameters can be placed into a configuration file with the path specified by the `-ConfigFilePath` parameter.  The config file can be formatted as YAML or JSON.

TODO: DON'T UNDERSTAND THIS SECTION.  WHAT is it trying to say?

The syntax defines:
* Use of Pascal case convention for variable names consistent with parameters on the command line
* A global namespace for values to be used across baselines and products (i.e., GlobalVars)
* Per product namespace for values related to that specific product (i.e., Aad, SharePoint)
* Namespace for each policy item within a product for variables related only to one policy item (i.e., MS.AAD.2.1v1)
* Use of YAML anchors and aliases following Don't Repeat Yourself (DRY) principle for repeated values and sections.  

## Sample Configuration Files

[Sample config files](https://github.com/cisagov/ScubaGear/tree/main/PowerShell/ScubaGear/Sample-Config-Files) are available in the repo.  Four of them are explained in more detail:

### Basic Use

The [basic use](https://github.com/cisagov/ScubaGear/blob/main/PowerShell/ScubaGear/Sample-Config-Files/basic_config.yaml) example only specifies a product name and an M365 environment in YAML.

ScubaGear can be invoked with this config file:

```powershell
# Invoke with config file
Invoke-SCuBA 
  -ConfigFilePath basic_config.yaml`
```

It can also be invoked while overriding the the `M365Environment` parameter:

```powershell
# Invoke with an override
Invoke-SCuBA 
  -M365Environment gcc 
  -ConfigFilePath minimal_config.yaml
```

### Typical Use

The [typical use](https://github.com/cisagov/ScubaGear/blob/main/PowerShell/ScubaGear/Sample-Config-Files/typical_config.yaml) example includes multiple products specified as a list and an M365 environment. Note that additional product values are commented out and will not be included, but are retained in the config file to easily add them back later. 

ScubaGear can be invoked with this config file:

```powershell
# Invoke with config file
Invoke-SCuBA 
  -ConfigFilePath typical_config.yaml
```

It can also be invoked with specifying authentication parameters:

```powershell
# Invoke with authentication
Invoke-SCuBA 
  -ConfigFilePath typical_config.yaml
  -Organization abcdef.example.com
  -AppID 0123456789abcdef01234566789abcde
  -CertificateThumbprint: fedcba9876543210fedcba9876543210fedcba98
```

### Credential Use

The [credential user](https://github.com/cisagov/ScubaGear/blob/main/PowerShell/ScubaGear/Sample-Config-Files/creds_config.yaml) example supplies credentials using a service principal, appId, and certificate thumbprint. (The associated private key is still required.)  Config files with sensitive data should be protected appropriately.

ScubaGear can be invoked with this config file:

```powershell
# Invoke with config file
Invoke-SCuBA 
  -ConfigFilePath creds_config.yaml
```

It can also be invoked by overriding the product names:

```powershell
# Invoke with a different product name
Invoke-SCuBA
  -ConfigFilePath typical_config.yaml
  -ProductNames defender
```

### Full Use

The [full config file](https://github.com/cisagov/ScubaGear/blob/main/PowerShell/ScubaGear/Sample-Config-Files/full_config.yaml) shows all of the global parameters supported by ScubaConfig specified in the config file. Any one of these parameters may be commented out. If not specified or if commented out, ScubaConfig will supply the default value unless overridden on the command line. This default value does not apply to authentication parameters.

```powershell
# Invoke without any overrides
Invoke-SCuBA 
  -ConfigFilePath full_config.yaml
```

## Empty Configuration File

ScubaGear's Support module also has functionality to generate an empty sample config file. Runnning the `New-Config` cmdlet will generate a full sample config called `SampleConfig.yaml` that can be filled out based on the guidance below. Parameters can be passed to the `New-Config` cmdlet to change values inside the sample config.

```powershell
# Create empty config file
New-Config
```

## AAD Conditional Access Policy Exemptions

TODO: WHAT IS THIS SAYING?

The ScubaGear `-ConfigFilePath` command line option allows users to define custom variables for use in policy assessments against the AAD baseline. These custom variables are used to exempt specific user and group exclusions from conditional access policy checks that normally would not pass if exclusions are present. These parameters support operational use cases for having backup or "break glass" account exclusions to global user policies without failing best practices. Any exemptions and their risks should be carefully considered and documented as part of an organization's cybersecurity risk management program process and practices.

## Config File Parameters

TODO: HERE'S AAD, WHERE ARE DEFENDER, EXO, and ALL THE OTHER SERVICES?  EITHER HAVE ALL OR HAVE NONE

### Aad

`Defines the AAD specific variables to specify user, group, and role exclusions that are documented exemptions to select conditional access policies (CAP) in the AAD configuration policy baselines. Users, groups, and roles are specified by their respective Universally Unique Identifier (UUID) in the tenant. This variable set is only needed if the agency has documented CAP exemptions.

**CapExclusions** - Supports both a Users and Groups list with each entry representing the UUID of a user or group that is approved by the agency to be included in a conditional access policy assignment exclusion. Adding an entry to this variable will prevent ScubaGear from failing the policy assessment due to the presence of the users and groups in an exclusion.

CapExclusions can be defined in the following policy namespaces:

- MS.AAD.1.1v1
- MS.AAD.2.1v1
- MS.AAD.2.3v1
- MS.AAD.3.1v1
- MS.AAD.3.2v1
- MS.AAD.3.3v1
- MS.AAD.3.6v1
- MS.AAD.3.7v1
- MS.AAD.3.8v1

**RoleExclusions** - Supports both a Users and Groups list with each entry representing the UUID of a user or group that is approved by the agency to be included in a role assignment. Adding an entry to this variable will prevent ScubaGear from failing the policy assessment due to the presence of a role assignment for those users and groups.

RoleExclusions can be defined in the following policy namespaces:

- MS.AAD.7.4v1

TODO:  Replace this example w a link to the config file in the repo.

The example below illustrates the syntax for defining user, group, and role exemptions to select policies. The syntax allows the use of a YAML anchor and alias to simplify formatting policies having the same documented exemptions. Items surrounded by chevrons are to be supplied by the user.

        Aad:
          MS.AAD.1.1v1: &CommonExclusions
            CapExclusions:
              Users:
                - <Exempted User 1 UUID>
                - <Exempted User 2 UUID>
              Groups:
                - <Exempted Group 1 UUID>
          MS.AAD.2.1v1:  *CommonExclusions
          MS.AAD.2.3v1:  *CommonExclusions
          MS.AAD.3.2v1:  *CommonExclusions
          MS.AAD.7.4v1:
            RoleExclusions:
              Users:
                - <Exempted User 3 UUID>
              Groups:
                - <Exempted Group 2 UUID>

# Parameters

TODO:  FOr ALL THE TABLES BELOW, find the correct values instead of ?.

The `ConfigFilePath` can be absolute or relative. IS THIS TRUE FOR ALL PATHy parameters? IF SO, SAY UP FRONT (or repeat everywhere).

TODO:  CLARIFY THIS.  What are the AUTH PARAMS/
IS THIS PRECENDENCE ONLY FOR AUTH PARAMS?

Each authentication parameter must be supplied either on the command line or in the config file if a non-interactive login is supplied. An authentication parameter may be present in both, but the command line will always take precedence. The parameters can be split between the config file and the command line.

The `Invoke-SCuBA` cmdlet has the following parameters:

TODO:  THIS IS NOT THE SET OF ALL PARAMETERS.  LIKE -APPID.  WHY DID WE SKIP SOME?
Version, DarkMode, Quiet, and MergeJson are also skipped.  Find ALL parameters AND ADD THIS TO THIS FILE.

PUT COMMANDS IN ALPHABETICAL ORDER

Each parameter SHOULD INCLUDE AT LEAST ONE EXAMPLE W the SCUBAGEAR COMMAND.

## Config File Path

| Parameter   | Value                                 |
|-------------|---------------------------------------|
| Optional    | Yes                                   |
| Datatype    | String                                |
| Default     | Directory where ScubaGear is executed |
| Config File | No                                    |

**ConfigFilePath** is the path of a configuration file that ScubaGear parses for input parameters. 

If `-ConfigFilePath` is specified, default values will be used for parameters that are not added to the config file. These default values are shown in the [full config file](https://github.com/cisagov/ScubaGear/blob/main/PowerShell/ScubaGear/Sample-Config-Files/full_config.yaml).  

TODO:  WHICH HAS PRECEDENCE?  CONFIG FILE OR COMMAND LINE PARAMETER?
I THINK IT"S THE COMMAND LINE PARAMETER.
DOES SG THROW AN ERROR OR WARNING?  IF NOT, MAKE THAT AN ISSUE, CAUSE IT SHOULD!

IT"S NOT OBVIOUS TO ME HOW THIS REDUCES NUMBER OF CONFIG FILES

Even if a parameter is specified in the configuration file, its value can be overriden by using the corresponding command line parameter.  

More information about the config files can be found on the [configuration page](configuration.md).

## Log In

| Parameter   | Value   |
|-------------|---------|
| Optional    | ?       |
| Datatype    | Boolean |
| Default     | ?       |
| Config File | Yes     |                                    |

**LogIn** enforces or bypasses authentication. If set to `$true`, ScubaGear will prompt the user to provide credentials to establish a connection to the specified M365 products in the `ProductNames` variable. This variable should typically be `$true`, as a connection is established in the current PowerShell terminal session with the first authentication. If another verification is run in the same PowerShell session, then this variable can be set to `$false` to bypass a second authenticate. 

> **NOTE**: Defender will ask for authentication even if this variable is set to `$false`

## Product Names

| Parameter   | Value                           |
|-------------|---------------------------------|
| Optional    | ?                               |
| Datatype    | Comma-separated list of strings |
| Default     | ?                               |
| Config File | Yes                             |  

IS "aad" still the correct FLAG?  SHOULD IT BE ENTRA?

**ProductNames** provides one or more M365 shortened product names that ScubaGear will assess. Acceptable values are:

| Product                                      | Product Name |
|----------------------------------------------|--------------|
| Azure Active Directory                       | aad          |
| Defender for Office 365                      | defender     |
| Exchange Online                              | exo          |
| Power Platform                               | powerplatform|
| SharePoint Online and OneDrive for Business  | sharepoint   |
| Microsoft Teams                              | teams        |

## M365 Environment

| Parameter   | Value      |
|-------------|------------|
| Optional    | ?          |
| Datatype    | String     |
| Default     | commercial |
| Config File | Yes        |  

**M365Environment** is used to authenticate to the various M365 commercial/government environments.

| Tenant                          | Value      |
|---------------------------------|------------|
| Non-government tenants          | commercial |
| Commercial cloud tenants        | gcc        |
| Commercial cloud tenants (high) | gcchigh    |
| Department of Defense tenants   | dod        |

## OPA Path

| Parameter   | Value      |
|-------------|------------|
| Optional    | ?          |
| Datatype    | String     |
| Default     | ?          |
| Config File | Yes        |  

**OPAPath** is the location of the Open Policy Agent (OPA) policy engine executable file. By default, the OPA policy engine executable embedded with this project is located in the project's root folder `"./"`, and for most cases this value will not need to be modified. 

## Out Path

| Parameter   | Value                                 |
|-------------|---------------------------------------|
| Optional    | Yes                                   |
| Datatype    | String                                |
| Default     | Directory where ScubaGear is executed |
| Config File | Yes                                   |  

**OutPath** is the location where the output JSON and the HTML report will be created. This parameter is only necessary if an alternate report folder path is desired. The folder will be created if it does not exist.

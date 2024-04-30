# Microsoft Graph

## Infinite AAD Signin Loop

TODO:  Does this occur with user permissions, SP permissions, or both?

Sometimes the AAD signin prompt sometimes get stuck in a loop. This is likely an issue with the connection to Microsoft Graph.

To fix the loop, run:

```powershell
# Disconnect from Microsoft Graph
Disconnect-MgGraph
```

Then run the tool again.

## Key not valid for use in specified state.

TODO:  When does this occur?

This is due to a [bug](https://github.com/microsoftgraph/msgraph-sdk-powershell/issues/554) in the Microsoft Authentication Library. The workaround is to delete broken configuration information by running this command (replace `{username}` with your username):

TODO:  What is in this folder?  What am I deleting?  What could go wrong?

```powershell
rm -r C:\Users\{username}\.graph
```

After deleting the `.graph` folder in your home directory, re-run ScubaGear, and the error should disappear.

## Could not load file or assembly 'Microsoft.Graph.Authentication'

TODO:  When does this occur?

This indicates that the authentication module is at a version level that conflicts with the MS Graph modules used by ScubaGear. Follow the instructions in the Installation section and execute the 'Initialize-SCuBA' cmdlet again. This will ensure that the module versions get synchronized with dependencies and then execute the tool again.

TODO:  Give an example of running this command or link the page that explains how/when to do this.

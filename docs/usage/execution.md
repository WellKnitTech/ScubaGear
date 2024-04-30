# Execution

ScubaGear is executed with the `Invoke-SCuBA` command.

## All Products

To assess all products:

```powershell
# Assess all products
Invoke-SCuBA
```

Alternatively, the `-ProductNames` flag can be used with a wildcard:

TODO:  WHY IS THIS HELPFUL?  DO WE REALLY NEED TO INCLUDE IT?  FEELS LIKE CLUTTER.

```powershell
# Assess all products
Invoke-SCuBA 
  -ProductNames *
```

> **NOTE**: This will not assess Power Platform because...

TODO:  WHY NOT POWER PLATFORM?

## One Product

To assess one product, use the `-ProductNames` flag:

TODO:  Is "add" STILL CORRECT?  OR IS IT ENTRA?

```powershell
# Assess AAD
Invoke-SCuBA 
  -ProductNames aad
```

The complete let is all product names can be found on the [parameters page](parameters.md).

## Multiple Products

To assess multiple products, add them to the `-ProductNames` flag:

TODO:  Is "add" STILL CORRECT?  OR IS IT ENTRA?

```powershell
# Assess AAD, SharePoint, and Teams
Invoke-SCuBA 
  -ProductNames aad, sharepoint, teams
```

## Custom Output Location

To change the location of the output:

```powershell
# Set custom output location
Invoke-SCuBA 
  -ProductNames aad 
  -OutPath C:\Users\johndoe\reports
```

## Non-interactive Mode

TODO:  WHICH MODE IS THE DEFAULT MODE?

To assess in the **non-interactive** mode using an application service principal and a certificate thumbprint:

TODO:  WHOA!  WHERE ARE INSTRUCTIONS For SETTING UP SERVICE PRINCIPAL AND CREATING A THUMBPRINT?  WHERE DOES THE APPID COME FROM?  
WHY IS THE ProductNames WILDCARD USED HERE?  IS IT NECESSARY?  HELPFUL EVEN?
WHY IS THERE NO QUOTES AROUND -Organization value?

```powershell
# Assess with service principal and thumbprint
Invoke-SCuBA -ProductNames * -CertificateThumbprint "<thumbprint>" -AppID "<appid>" -Organization <tenant-name>.onmicrosoft.com
```

For more information, see the [parameters page](parameters.md) or run `Get-Help`:

```powershell
# Get ScubaGear help
Get-Help 
  -Name Invoke-SCuBA 
  -Full
```
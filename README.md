# Script Usage Instructions

This script is designed to retrieve web bindings (IIS) and display them in a grouped and formatted table. The script allows for the specification of a domain to filter the results.

## Prerequisites

- Windows PowerShell
- Access to the `Get-WebBinding` cmdlet (requires the WebAdministration module)

## Usage

Open a PowerShell console and run the code from [domain-binding-info](domain-binding-info)

### How It Works

The script performs the following steps:

1. Sets the initial value of the `$domain` variable to an empty string.
2. Retrieves all web bindings using the `Get-WebBinding` cmdlet.
3. Filters the web bindings based on the specified domain using the `Where-Object` cmdlet and the `-like` operator.
4. For each matching web binding, extracts the name and binding information.
5. Creates a custom PowerShell object with properties for the name and binding.
6. Groups the web bindings by name using the `Group-Object` cmdlet.
7. Formats and displays the results in a table using the `Format-Table` cmdlet.

### Examples

- If `$domain` is left empty (`""`), all web bindings will be retrieved and displayed:

```powershell
$domain = ""
```
Example output:

```powershell
Name       Bindings
----       --------
Default    *
Example    example.com:80
           example.org:443
```

If a domain is specified, only the web bindings containing the specified domain will be retrieved and displayed. For example, if `$domain` is set to `"example.com"`, only the web bindings with `example.com` will be shown:

```powershell
$domain = "example.com"
```

```powershell
Name       Bindings
----       --------
Example    example.com:80
```


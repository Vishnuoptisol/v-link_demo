# Web.Release.config Documentation

## Overview

`Web.Release.config` is a configuration transformation file used in ASP.NET applications to modify the base `Web.config` file when deploying to a Release environment. It leverages XML Document Transform (XDT) syntax to apply specific changes to the main configuration file during the build and deployment process, ensuring that the application runs with appropriate settings in a production environment.

This file is part of the MixERP.Net.FrontEnd project and is designed to transform the [Web.config](Web.config.md) file when the application is built in Release mode. Its primary purpose is to disable debug compilation, which improves performance in production environments.

## File Structure Documentation

### XML Declaration

```xml
<?xml version="1.0"?>
```

The standard XML declaration indicating the document conforms to XML 1.0 specification.

### Copyright Notice

The file contains a copyright notice that specifies:
- Copyright holder: Binod Nepal, Mix Open Foundation (http://mixof.org)
- License: Mozilla Public License, v. 2.0
- License information location: http://mozilla.org/MPL/2.0/

### Configuration Element

```xml
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
```

The root configuration element with the XML Document Transform namespace declaration. This namespace provides access to the transformation directives used to modify the base [Web.config](Web.config.md) file.

### System.Web Element

```xml
<system.web>
  <compilation xdt:Transform="RemoveAttributes(debug)" />
</system.web>
```

This section contains transformations applied to the `system.web` element in the base configuration:

- `<compilation xdt:Transform="RemoveAttributes(debug)" />`: This transformation removes the `debug` attribute from the `compilation` element. In standard [Web.config](Web.config.md) files, this attribute is typically set to `true` during development to enable debugging. Removing it in the release configuration effectively sets it to `false`, which is appropriate for production environments as it improves performance.

### Commented Examples

The file includes several commented examples demonstrating other transformation techniques:

1. Connection string transformation example:
   ```xml
   <connectionStrings>
     <add name="MyDB" 
       connectionString="Data Source=ReleaseSQLServer;Initial Catalog=MyReleaseDB;Integrated Security=True" 
       xdt:Transform="SetAttributes" xdt:Locator="Match(name)"/>
   </connectionStrings>
   ```
   This example shows how to modify a connection string for a specific database when deploying to a production environment.

2. Custom errors transformation example:
   ```xml
   <customErrors defaultRedirect="GenericError.htm"
     mode="RemoteOnly" xdt:Transform="Replace">
     <error statusCode="500" redirect="InternalError.htm"/>
   </customErrors>
   ```
   This example demonstrates replacing the entire `customErrors` section to configure error handling in a production environment, redirecting users to appropriate error pages.

## Related Files

This transformation file works in conjunction with:

- [Web.config](Web.config.md): The base configuration file that gets transformed
- [Web.Debug.config](Web.Debug.config.md): The transformation file used for Debug builds

## Usage

The Web.Release.config file is automatically applied during the build process when the project is built using the Release configuration. The transformations in this file are processed by the MSBuild process, which generates a transformed Web.config in the output directory.

No manual intervention is typically required to apply these transformations, as they are handled by the build system when deploying or publishing the application in Release mode.
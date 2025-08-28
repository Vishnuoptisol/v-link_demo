# Web.Debug.config Documentation

## Overview

`Web.Debug.config` is a configuration transformation file for ASP.NET applications, specifically designed for debug environments. This file contains XML Document Transform (XDT) instructions that modify the base [Web.config](Web.config.md) file when the application is deployed in debug mode. The file includes copyright information from Mix Open Foundation and is governed by the Mozilla Public License, v. 2.0.

## File Structure and Purpose

The `Web.Debug.config` file serves as a transformation template that applies specific configuration changes when the application is compiled or published in debug configuration. These transformations are processed by Microsoft's XDT (XML Document Transform) system to modify the base configuration.

### Configuration Elements

#### XML Declaration
```xml
<?xml version="1.0"?>
```
This line defines the XML version used in the document.

#### Copyright Notice
The file contains a copyright notice in an XML comment block indicating that it is copyrighted by Binod Nepal and the Mix Open Foundation, and is available under the Mozilla Public License, v. 2.0.

#### Root Configuration Element
```xml
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
```
This is the root element of the configuration file, with the XDT namespace declaration that enables transformation directives.

### Transformation Examples

The file includes commented-out examples demonstrating how to use transformation directives:

#### Connection String Example
```xml
<!--
<connectionStrings>
  <add name="MyDB" 
    connectionString="Data Source=ReleaseSQLServer;Initial Catalog=MyReleaseDB;Integrated Security=True" 
    xdt:Transform="SetAttributes" xdt:Locator="Match(name)"/>
</connectionStrings>
-->
```
This example shows how to transform a connection string named "MyDB" by changing its attributes when deploying to a debug environment.

#### Custom Errors Example
```xml
<!--
<customErrors defaultRedirect="GenericError.htm"
  mode="RemoteOnly" xdt:Transform="Replace">
  <error statusCode="500" redirect="InternalError.htm"/>
</customErrors>
-->
```
This example demonstrates how to replace the entire `<customErrors>` section in the base configuration file.

### System.Web Section
```xml
<system.web>
  <!-- Transformation examples for system.web section -->
</system.web>
```
This section is where transformations related to ASP.NET settings would be defined, though in this file, only commented examples are provided without active transformations.

## Relationship with Other Configuration Files

`Web.Debug.config` works in conjunction with:

- [Web.config](Web.config.md) - The base configuration file that applies to all environments
- [Web.Release.config](Web.Release.config.md) - The transformation file for release environments

## Usage

When publishing the MixERP.Net.FrontEnd application with the Debug configuration:

1. The build system reads the base Web.config file
2. It applies the transformations specified in Web.Debug.config
3. The resulting transformed configuration is deployed with the application

This allows developers to maintain different configuration settings between development (debug) and production (release) environments without manually editing configuration files during deployment.

## Notes

- This file contains only examples and commented-out transformations, indicating that the MixERP application may not require specific debug-mode configuration changes
- To implement actual transformations, the XML comments would need to be removed and the transformation directives properly configured

## See Also

- [Web.config](Web.config.md)
- [Web.Release.config](Web.Release.config.md)
- [Global.asax](Global.asax.md)
- [Global.asax.cs](Global.asax.cs.md)
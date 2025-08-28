# Web.config.backup Documentation

## Overview

This file serves as a backup configuration file for the MixERP.Net.FrontEnd web application. The web.config file is a core configuration file in ASP.NET applications that controls various aspects of the application, including database connections, authentication settings, page rendering, and web service configurations. This backup version contains essential configuration parameters including database connection details, authentication settings, and various system-wide behaviors.

## Configuration Sections

### Connection Strings

The connection strings section is present but empty in this backup configuration file. Connection strings typically define the parameters needed to connect to databases, but in this case, connection details are specified through application settings instead.

```xml
<connectionStrings />
```

### Application Settings

The appSettings section contains key database configuration parameters:

- **Server**: Specifies the database server (set to "localhost")
- **Database**: Defines the database name to connect to (set to "mixerp")
- **UserId**: Database login username (set to "postgres")
- **Password**: Database login password (set to "binod")
- **DisplayError**: Boolean flag that controls whether errors should be displayed to users (set to "true")

### System.Web Section

This section contains core ASP.NET configuration elements:

#### Compilation

```xml
<compilation debug="true" targetFramework="4.0" />
```
- Sets debug mode to true, enabling detailed error information
- Targets .NET Framework 4.0

#### Session State

```xml
<sessionState timeout="259200" />
```
- Sets session timeout to 259,200 minutes (180 days), which is an unusually long session timeout

#### Authentication

```xml
<authentication mode="Forms">
    <forms loginUrl="~/SignIn.aspx" timeout="2880" defaultUrl="~/Account/Index.aspx" />
</authentication>
```
- Configures Forms Authentication
- Login page is set to [SignIn.aspx](SignIn.aspx.md)
- Session timeout is set to 2,880 minutes (48 hours)
- Default redirect URL after successful login is set to "~/Account/Index.aspx"

#### Pages Configuration

```xml
<pages theme="MixERP" enableViewState="false" enableEventValidation="false" enableViewStateMac="false" clientIDMode="Static" controlRenderingCompatibilityVersion="4.0">
```
- Uses the "MixERP" theme from [App_Themes/MixERP](App_Themes/MixERP/Default.css.md)
- Disables ViewState, EventValidation, and ViewStateMac for better performance but reduced security
- Sets clientIDMode to "Static" to make client-side scripting easier
- Sets control rendering compatibility to 4.0

#### Custom Controls

The pages section also registers several custom user controls:

```xml
<controls>
    <add tagPrefix="webdiyer" namespace="Wuqi.Webdiyer" assembly="AspNetPager" />
    <add tagPrefix="pes" tagName="Form" src="~/UserControls/Forms/FormControl.ascx" />
    <add tagPrefix="pes" tagName="Product" src="~/UserControls/Products/ProductControl.ascx" />
    <add tagPrefix="pes" tagName="DateTextBox" src="~/UserControls/DateTextBox.ascx" />
    <add tagPrefix="ajaxToolkit" assembly="AjaxControlToolkit" namespace="AjaxControlToolkit" />
</controls>
```

This registers:
- AspNetPager control for pagination
- Form control from [FormControl.ascx](UserControls/Forms/FormControl.ascx.md)
- Product control from [ProductControl.ascx](UserControls/Products/ProductControl.ascx.md)
- DateTextBox control from [DateTextBox.ascx](UserControls/DateTextBox.ascx.md)
- AjaxControlToolkit controls

#### Membership, Profile, and Role Management

The configuration includes standard ASP.NET membership, profile, and role management providers, though the role manager is disabled:

```xml
<roleManager enabled="false">
```

#### Web Services

Web services configuration allows both HTTP GET and POST protocols:

```xml
<webServices>
    <protocols>
        <add name="HttpGet"/>
        <add name="HttpPost"/>
    </protocols>
</webServices>
```

### System.Web.Extensions Section

This section configures ASP.NET AJAX extensions:

```xml
<system.web.extensions>
    <scripting>
        <webServices>
            <jsonSerialization maxJsonLength="5000000" />
        </webServices>
    </scripting>
</system.web.extensions>
```

The configuration sets a large JSON serialization size limit (5,000,000 characters), which allows for transferring large amounts of data in AJAX calls.

### System.WebServer Section

This section configures IIS-specific settings:

```xml
<system.webServer>
    <modules runAllManagedModulesForAllRequests="true">
    </modules>
</system.webServer>
```

- Enables all managed modules to run for all request types, which can impact performance but increases compatibility

## Licensing Information

The file includes a GPL v3 license notice at the top, indicating that the MixERP application is released under the GNU General Public License version 3 or later. The copyright is attributed to Binod Nepal, Planet Earth Solutions Pvt. Ltd., Kathmandu.

## Relationship to Main Web.config

As a backup file, this configuration is likely intended to serve as a reference or fallback configuration that can be restored if the main [Web.config](Web.config.md) becomes corrupted or needs to be rolled back. The presence of actual database credentials in this backup file suggests that it may contain a working configuration that was backed up at some point during development or deployment.
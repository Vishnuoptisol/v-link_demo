# Web.config Documentation

## Overview

The `Web.config` file is the main configuration file for the MixERP.Net.FrontEnd ASP.NET application. It configures system behavior, authentication, database connections, custom controls, and various application parameters. This configuration file is structured in XML format and contains multiple sections defining both standard ASP.NET behaviors and MixERP-specific settings.

## Configuration Sections

### License Information

The file begins with a copyright notice for Binod Nepal and Mix Open Foundation (http://mixof.org), indicating the code is distributed under Mozilla Public License v. 2.0.

### Config Sections Definition

The `configSections` element defines custom configuration section handlers:

- **MixERPParameters**: Uses the standard .NET `NameValueFileSectionHandler` to manage application parameters
- **MixERPDbParameters**: Handles database connection parameters
- **MixERPSwitches**: Manages application feature switches

### External Configuration Files

The configuration utilizes external XML files to store settings:

- **MixERPDbParameters**: References `Resource\Configuration\DbParameters.xml`
- **MixERPParameters**: References `Resource\Configuration\Parameters.xml`
- **MixERPSwitches**: References `Resource\Configuration\Switches.xml`

### Application Settings

The `appSettings` section defines key database connection and debug settings:

- **Server**: PostgreSQL server location (localhost)
- **Database**: Database name (mixerp)
- **UserId**: Database user (postgres)
- **Password**: Database password
- **DisplayError**: Error display flag (true)
- **Microsoft Visual Studio Team Systems** settings for development and backup

### System.Web Configuration

#### Session State

- **Mode**: InProc
- **Cookieless**: UseCookies
- **Timeout**: 60 minutes

#### Authentication

- **Mode**: Forms
- **Login URL**: ~/SignIn.aspx
- **Timeout**: 60 minutes
- **Sliding Expiration**: Enabled
- **Default URL**: ~/Dashboard/Index.aspx

#### Page Configuration

- **.NET Framework Target**: 4.0 (Mono Profile)
- **ViewState**: Disabled
- **ViewStateMac**: Disabled 
- **Event Validation**: Disabled
- **Theme**: MixErp
- **Client ID Mode**: Static

#### Custom Controls Registration

The configuration registers numerous custom user controls with the `mixerp` prefix:

- **Form**: [FormControl.ascx](UserControls/Forms/FormControl.md)
- **Product**: [ProductControl.ascx](UserControls/Products/ProductControl.md)
- **ProductView**: [ProductViewControl.ascx](UserControls/Products/ProductViewControl.md)
- **DateTextBox**: [DateTextBox.ascx](UserControls/DateTextBox.md)
- **ReportHeader**: [Header.ascx](UserControls/Reporting/Header.md)
- **Report**: [ReportControl.ascx](UserControls/ReportControl.md)
- **TransactionChecklist**: [TransactionChecklistControl.ascx](UserControls/TransactionChecklistControl.md)

And several widgets:
- **AlertsWidget**: [AlertsWidget.ascx](UserControls/Widgets/AlertsWidget.md)
- **CurrentOfficeSalesByMonthWidget**: [CurrentOfficeSalesByMonthWidget.ascx](UserControls/Widgets/CurrentOfficeSalesByMonthWidget.md)
- **LinksWidget**: [LinksWidget.ascx](UserControls/Widgets/LinksWidget.md)
- **OfficeInformationWidget**: [OfficeInformationWidget.ascx](UserControls/Widgets/OfficeInformationWidget.md)
- **SalesByOfficeWidget**: [SalesByOfficeWidget.ascx](UserControls/Widgets/SalesByOfficeWidget.md)
- **TopSellingProductOfAllTimeCurrentWidget**: [TopSellingProductOfAllTimeCurrentWidget.ascx](UserControls/Widgets/TopSellingProductOfAllTimeCurrentWidget.md)
- **TopSellingProductOfAllTimetWidget**: [TopSellingProductOfAllTimetWidget.ascx](UserControls/Widgets/TopSellingProductOfAllTimetWidget.md)
- **WorkflowWidget**: [WorkflowWidget.ascx](UserControls/Widgets/WorkflowWidget.md)

Also registers the AjaxControlToolkit with the prefix "AjaxCTK".

#### Web Services Configuration

- Enabled protocols: HttpGet, HttpPost

### System.Web.Extensions Configuration

- **JSON Serialization**: Maximum length set to 5,000,000 characters to accommodate large data transfers

### IIS Configuration (system.webServer)

- **Modules**: All managed modules run for all requests
- **Validation**: Integrated mode configuration validation is disabled
- **Handlers**: Custom handlers section present (empty in the current configuration)

## Related Files

This configuration file references several external configuration files:

- [DbParameters.xml](Resource/Configuration/DbParameters.md) - Database connection parameters
- [Parameters.xml](Resource/Configuration/Parameters.md) - Application parameters
- [Switches.xml](Resource/Configuration/Switches.md) - Feature switches and toggles

## Integration Points

The Web.config integrates with:

- [SignIn.aspx](SignIn.md) - The login page for the application
- [Dashboard/Index.aspx](Dashboard/Index.md) - The default landing page after authentication
- Various user controls in the UserControls directory
- External libraries including AjaxControlToolkit and AspNetPager

## Security Considerations

The configuration contains sensitive information:
- Database credentials in plaintext (server, database, username, password)
- Forms authentication settings
- Session timeout values

In a production environment, these settings should be properly secured and potentially moved to protected configuration sections.
# ConvertLeadToOpportunity.aspx Documentation

## Overview

The `ConvertLeadToOpportunity.aspx` file is part of the MixERP CRM (Customer Relationship Management) module. It provides a web interface for converting leads into opportunities within the MixERP system. This functionality is essential in the sales pipeline, allowing users to progress potential customers (leads) to the next stage as sales opportunities when they show genuine interest in the company's products or services.

The file is structured as an ASP.NET Web Forms page that inherits from the [ContentMaster.Master](../ContentMaster.Master.md) master page, which provides the common layout and styling for the application.

## File Structure

The file follows the standard ASP.NET Web Forms page structure with content placeholders that are defined in the master page:

1. `ScriptContentPlaceHolder` - For JavaScript includes and script blocks
2. `StyleSheetContentPlaceHolder` - For CSS includes and style blocks
3. `BodyContentPlaceHolder` - For the main content of the page
4. `BottomScriptContentPlaceHolder` - For scripts that need to be loaded at the bottom of the page

Currently, all content placeholders are empty, which suggests that either:
- The implementation details are provided in the code-behind file [ConvertLeadToOpportunity.aspx.cs](ConvertLeadToOpportunity.aspx.cs.md)
- The page is a placeholder awaiting further implementation

## Class Documentation

The page class is defined in the code-behind file [ConvertLeadToOpportunity.aspx.cs](ConvertLeadToOpportunity.aspx.cs.md) and inherits from `System.Web.UI.Page`. The class name is `MixERP.Net.FrontEnd.CRM.ConvertLeadToOpportunity`.

## Page Relationships

This page is part of the CRM module workflow and is likely related to:

- [CRM/Lead.aspx](Lead.aspx.md) - Where leads are initially created and managed
- [CRM/LeadFollowup.aspx](LeadFollowup.aspx.md) - For tracking interactions with leads
- [CRM/Opportunity.aspx](Opportunity.aspx.md) - Where opportunities are managed after conversion

## License Information

The code is licensed under the Mozilla Public License, v. 2.0, as indicated by the copyright header. The copyright is held by Binod Nepal, Mix Open Foundation (http://mixof.org).

## Technical Implementation Notes

As this is an ASP.NET Web Forms page, the actual form elements and business logic would typically be implemented in the code-behind file. The page leverages the ASP.NET content placeholder model to integrate with the site's master page structure.

For detailed information on how the lead-to-opportunity conversion is implemented, including any specific business rules, validation, or database interactions, please refer to the code-behind documentation in [ConvertLeadToOpportunity.aspx.cs](ConvertLeadToOpportunity.aspx.cs.md).
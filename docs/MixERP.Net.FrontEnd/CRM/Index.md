# MixERP.Net.FrontEnd.CRM.Index.aspx Documentation

## Overview

`Index.aspx` serves as the landing page for the Customer Relationship Management (CRM) module in the MixERP.Net application. This page provides the entry point to CRM functionality and displays a navigational menu for accessing various CRM features. The page is structured using ASP.NET Web Forms technology and inherits from the [MenuMaster.Master](../MenuMaster.Master.md) master page, which provides a consistent layout and navigation structure across the application.

## Page Structure

### Master Page

- **Master Page**: [MenuMaster.Master](../MenuMaster.Master.md)
- **Code Behind**: [Index.aspx.cs](Index.aspx.cs.md)

### Content Placeholders

The page utilizes four content placeholders defined in the master page:

1. **ScriptContentPlaceHolder** (`Content1`) - Reserved for JavaScript scripts specific to this page (empty in current implementation)
2. **StyleSheetContentPlaceHolder** (`Content2`) - Reserved for CSS stylesheets specific to this page (empty in current implementation)
3. **BodyContentPlaceHolder** (`Content3`) - Contains the main content of the page:
   - A heading labeled "Customer Relationship Management"
   - A horizontal rule (`<hr>`) for visual separation
   - A `MenuLiteral` control that dynamically renders the CRM menu items
4. **BottomScriptContentPlaceHolder** (`Content4`) - Reserved for JavaScript that should be loaded at the bottom of the page (empty in current implementation)

### Server Controls

- **MenuLiteral** (`asp:Literal`):
  - **ID**: `MenuLiteral`
  - **Type**: ASP.NET Literal control
  - **Purpose**: Dynamically populated with CRM navigation menu HTML in the code-behind

## Functionality

This page acts as a hub for accessing different CRM features within the MixERP application. The main functionality comes from the dynamically generated menu, which likely includes links to:

- [Lead.aspx](Lead.aspx.md) - Lead management
- [LeadFollowup.aspx](LeadFollowup.aspx.md) - Lead followup activities
- [Opportunity.aspx](Opportunity.aspx.md) - Opportunity management
- [OpportunityFollowup.aspx](OpportunityFollowup.aspx.md) - Opportunity followup activities
- [ConvertLeadToOpportunity.aspx](ConvertLeadToOpportunity.aspx.md) - Convert leads to opportunities

The page also likely includes links to CRM setup pages:
- [Setup/LeadSources.aspx](Setup/LeadSources.aspx.md) - Manage lead sources
- [Setup/LeadStatuses.aspx](Setup/LeadStatuses.aspx.md) - Manage lead statuses
- [Setup/OpportunityStages.aspx](Setup/OpportunityStages.aspx.md) - Manage opportunity stages

## License Information

The code is licensed under the Mozilla Public License, v. 2.0, and is attributed to Binod Nepal, Mix Open Foundation (http://mixof.org).

## Related Files

- [Index.aspx.cs](Index.aspx.cs.md) - The code-behind file that contains the server-side logic
- [Index.aspx.designer.cs](Index.aspx.designer.cs.md) - Designer file that defines the controls used on the page
- [MenuMaster.Master](../MenuMaster.Master.md) - The master page that provides the layout for this page

## Usage

This page is accessed when a user navigates to the CRM module in the MixERP application. Users can then select from the available menu items to access different CRM functionalities.
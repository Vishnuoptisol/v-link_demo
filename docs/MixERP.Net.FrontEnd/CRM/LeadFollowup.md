# LeadFollowup.aspx Documentation

## Overview

`LeadFollowup.aspx` is an ASP.NET Web Form within the Customer Relationship Management (CRM) module of MixERP. This page is designed to track and manage follow-up activities related to sales leads. It follows MixERP's master page structure, inheriting from [ContentMaster.Master](../ContentMaster.Master.md) to maintain consistent design and functionality across the application.

The page is part of MixERP's CRM module, which also includes other lead management features such as [Lead.aspx](Lead.aspx.md) and [ConvertLeadToOpportunity.aspx](ConvertLeadToOpportunity.aspx.md).

## Page Structure

### Master Page

This page inherits from [ContentMaster.Master](../ContentMaster.Master.md), which provides the standard layout, navigation, and shared resources for MixERP's content pages.

### Content Placeholders

The page defines four content placeholders that correspond to the content areas defined in the master page:

1. **ScriptContentPlaceHolder**: Reserved for JavaScript code specific to this page.
2. **StyleSheetContentPlaceHolder**: Reserved for CSS styles specific to this page.
3. **BodyContentPlaceHolder**: The main content area of the page.
4. **BottomScriptContentPlaceHolder**: Reserved for JavaScript code that needs to be loaded after the page content.

Currently, all content placeholders are empty, indicating that the page's implementation may be in progress or that the functionality is defined in the code-behind file [LeadFollowup.aspx.cs](LeadFollowup.aspx.cs.md).

## Page Class

The page is implemented by the `MixERP.Net.FrontEnd.CRM.LeadFollowup` class defined in [LeadFollowup.aspx.cs](LeadFollowup.aspx.cs.md).

## Licensing

The code is licensed under the Mozilla Public License, v. 2.0, as indicated in the file header comment. This is consistent with MixERP's open-source nature and the copyright is attributed to Binod Nepal, Mix Open Foundation (http://mixof.org).

## Related Files

- [LeadFollowup.aspx.cs](LeadFollowup.aspx.cs.md): Code-behind file containing the server-side logic for this page.
- [LeadFollowup.aspx.designer.cs](LeadFollowup.aspx.designer.cs.md): Auto-generated file containing control declarations for this page.
- [Lead.aspx](Lead.aspx.md): Page for creating and managing leads.
- [ConvertLeadToOpportunity.aspx](ConvertLeadToOpportunity.aspx.md): Page for converting qualified leads to sales opportunities.
- [OpportunityFollowup.aspx](OpportunityFollowup.aspx.md): Similar page for following up on opportunities.

## Integration with CRM Module

This page is part of the MixERP CRM module, which includes the following key components:

- Lead management
- Lead tracking and follow-up
- Opportunity management
- Lead source and status management

The page likely works in conjunction with the CRM setup pages found in the [Setup](Setup/LeadSources.aspx.md) directory, which define the configuration for lead sources, statuses, and opportunity stages.

## Usage

While the page content is currently empty in the ASPX file, the page is designed to allow users to:

1. Record follow-up activities related to leads
2. Schedule new follow-up actions
3. Document communication with leads
4. Update lead status based on follow-up results

The actual implementation of these features would be found in the [LeadFollowup.aspx.cs](LeadFollowup.aspx.cs.md) code-behind file.
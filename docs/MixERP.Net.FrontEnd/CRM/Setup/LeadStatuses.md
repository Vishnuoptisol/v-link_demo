# LeadStatuses.aspx Documentation

## Overview
The `LeadStatuses.aspx` page is part of the MixERP.Net.FrontEnd Customer Relationship Management (CRM) module setup. This page provides a user interface for managing lead statuses within the CRM system. Lead statuses help track and categorize the current state of leads in a sales pipeline, such as "New", "Contacted", "Qualified", or "Lost".

## Page Structure
This ASP.NET Web Form uses the [ContentMaster.Master](../../ContentMaster.Master.md) as its master page and consists of four content sections:
1. Script content section
2. Style sheet content section
3. Body content section
4. Bottom script content section

## Content Sections

### Script Content Section
```html
<asp:Content ID="Content1" ContentPlaceHolderID="ScriptContentPlaceHolder" runat="server">
</asp:Content>
```
This content section is intended for page-specific JavaScript, but remains empty in this implementation.

### Style Sheet Content Section
```html
<asp:Content ID="Content2" ContentPlaceHolderID="StyleSheetContentPlaceHolder" runat="server">
</asp:Content>
```
This content section is intended for page-specific CSS styles, but remains empty in this implementation.

### Body Content Section
```html
<asp:Content ID="Content3" ContentPlaceHolderID="BodyContentPlaceHolder" runat="server">
    <mixerp:Form ID="LeadStatusForm" runat="server" 
        DenyAdd="false" DenyDelete="false" DenyEdit="false" 
        KeyColumn="lead_status_id"
        PageSize="10" Width="1000" 
        TableSchema="crm" Table="lead_statuses" 
        ViewSchema="crm" View="lead_statuses" 
        Text="<%$Resources:Titles, LeadStatuses %>" />
</asp:Content>
```
This section contains the main content of the page, which includes a custom `mixerp:Form` control with the following properties:
- **ID**: LeadStatusForm
- **Access Controls**:
  - DenyAdd: false - Allows adding new lead statuses
  - DenyDelete: false - Allows deleting existing lead statuses
  - DenyEdit: false - Allows editing existing lead statuses
- **Data Structure**:
  - KeyColumn: lead_status_id - The primary key column in the database
  - TableSchema: crm - The database schema name
  - Table: lead_statuses - The database table name
  - ViewSchema: crm - The schema of the database view
  - View: lead_statuses - The database view name for displaying data
- **UI Configuration**:
  - PageSize: 10 - Number of records displayed per page
  - Width: 1000 - Width of the form in pixels
  - Text: Retrieves the localized string for "LeadStatuses" from the [Titles.resx](../../App_GlobalResources/Titles.resx.md) resource file

### Bottom Script Content Section
```html
<asp:Content ID="Content4" ContentPlaceHolderID="BottomScriptContentPlaceHolder" runat="server">
</asp:Content>
```
This content section is intended for page-specific JavaScript that should be loaded at the bottom of the page, but remains empty in this implementation.

## Related Files
- [LeadStatuses.aspx.cs](./LeadStatuses.aspx.cs.md) - The code-behind file for this page
- [LeadStatuses.aspx.designer.cs](./LeadStatuses.aspx.designer.cs.md) - The auto-generated designer file
- [ContentMaster.Master](../../ContentMaster.Master.md) - The master page used by this page
- [LeadSources.aspx](./LeadSources.aspx.md) - Related CRM setup page for managing lead sources
- [OpportunityStages.aspx](./OpportunityStages.aspx.md) - Related CRM setup page for managing opportunity stages
- [Lead.aspx](../Lead.aspx.md) - The page for creating and managing leads that uses these statuses
- [UserControls/Forms/FormControl.ascx](../../UserControls/Forms/FormControl.ascx.md) - The form control used in this page

## Database Schema
This page interacts with the following database objects:
- Schema: `crm`
- Table: `lead_statuses`
- View: `lead_statuses`
- Primary Key: `lead_status_id`

## Usage
The Lead Statuses page allows users to:
1. View a list of existing lead statuses in the CRM system
2. Add new lead statuses
3. Edit properties of existing lead statuses
4. Delete lead statuses that are no longer needed

The page displays 10 records per page and provides navigation controls to browse through additional pages if there are more records.

## Copyright
This code is released under the Mozilla Public License, v. 2.0. The copyright is held by Binod Nepal, Mix Open Foundation.
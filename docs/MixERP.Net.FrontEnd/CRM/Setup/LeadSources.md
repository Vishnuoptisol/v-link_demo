# Lead Sources Page Documentation

## Overview

The `LeadSources.aspx` file is a web form that provides functionality for managing lead sources in the MixERP CRM module. It enables users to view, add, edit, and delete lead source records. Lead sources represent the various channels through which potential leads enter the CRM system, such as website inquiries, referrals, trade shows, or advertising campaigns.

The page is implemented as an ASP.NET Web Form that utilizes MixERP's custom `Form` control to provide a standardized data management interface.

## Page Structure

### Master Page
The page uses the [ContentMaster.Master](../../../ContentMaster.Master.md) as its master page, providing consistent layout and navigation across the application.

### Content Placeholders
The page includes four content placeholders:
- `ScriptContentPlaceHolder`: Reserved for JavaScript includes
- `StyleSheetContentPlaceHolder`: Reserved for CSS stylesheet includes
- `BodyContentPlaceHolder`: Contains the main form control
- `BottomScriptContentPlaceHolder`: Reserved for scripts to be placed at the bottom of the page

## Form Control Implementation

The page primarily consists of a single custom MixERP Form control (`mixerp:Form`) which handles all data operations. This control connects to the CRM database and manages the CRUD operations for lead sources.

### Form Control Properties

| Property | Value | Description |
|----------|-------|-------------|
| ID | LeadSourceForm | Unique identifier for the form control |
| DenyAdd | false | Allows users to add new lead source records |
| DenyDelete | false | Allows users to delete existing lead source records |
| DenyEdit | false | Allows users to edit existing lead source records |
| KeyColumn | lead_source_id | Primary key column name for the lead_sources table |
| PageSize | 10 | Number of records to display per page |
| Width | 1000 | Width of the form control (pixels) |
| TableSchema | crm | Database schema name containing the lead_sources table |
| Table | lead_sources | Database table name for lead sources |
| ViewSchema | crm | Schema name for the view used to display lead sources |
| View | lead_sources | View name used to display lead sources |
| Text | <%$Resources:Titles, LeadSources %> | Page title, retrieved from localized resource files |

## Database Integration

The form interacts with the `lead_sources` table in the `crm` schema. The view and table have the same name in this implementation, indicating that the view likely represents a direct or slightly modified representation of the underlying table.

## User Interface Features

Based on the form control configuration:

1. The interface displays lead source records in a paginated grid format, with 10 records per page
2. Users can add new lead sources via an add button/interface
3. Users can edit existing lead source records
4. Users can delete lead source records
5. The form has a fixed width of 1000 pixels
6. The page title is localized, pulled from the application's resource files

## Related Files

- [ContentMaster.Master](../../../ContentMaster.Master.md): Master page providing the layout structure
- [LeadSources.aspx.cs](./LeadSources.aspx.cs.md): Code-behind file that defines the page behavior
- [LeadSources.aspx.designer.cs](./LeadSources.aspx.designer.cs.md): Auto-generated file that defines the controls
- [LeadStatuses.aspx](./LeadStatuses.aspx.md): Related page for managing lead statuses
- [OpportunityStages.aspx](./OpportunityStages.aspx.md): Related page for managing opportunity stages

## Licensing Information

The code is provided under the Mozilla Public License, v. 2.0, as indicated in the copyright notice. The copyright is attributed to Binod Nepal, Mix Open Foundation (http://mixof.org).

## Page Navigation

This page would typically be accessed through the CRM module's setup section, as indicated by its location in the directory structure (`CRM/Setup/`).
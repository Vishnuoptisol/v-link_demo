# OpportunityStages.aspx Documentation

## Overview

`OpportunityStages.aspx` is a web form component of the MixERP.Net CRM module that provides a user interface for managing opportunity stages in the Customer Relationship Management system. This page allows users to view, add, edit, and delete opportunity stages that represent different phases in the sales pipeline or opportunity lifecycle.

The page uses the `FormControl` component to handle data display and CRUD operations (Create, Read, Update, Delete) against the opportunity stages database table.

## Page Structure

The page is structured using the ASP.NET Web Forms framework and inherits from the [ContentMaster.Master](../../ContentMaster.Master.md) master page, which provides the consistent layout and navigation structure for the application.

### Master Page

- **Master Page File**: [ContentMaster.Master](../../ContentMaster.Master.md)
- **Code Behind**: [OpportunityStages.aspx.cs](./OpportunityStages.aspx.cs.md)

### Content Placeholders

The page defines content for four different content placeholders defined in the master page:

1. **ScriptContentPlaceHolder**: For JavaScript content (currently empty)
2. **StyleSheetContentPlaceHolder**: For CSS styling (currently empty)
3. **BodyContentPlaceHolder**: Contains the main form component
4. **BottomScriptContentPlaceHolder**: For scripts to be loaded at the bottom of the page (currently empty)

## Form Component

The page contains a single Form control from MixERP's custom control library that handles all the database operations and UI rendering for the opportunity stages data.

### Form Control Properties

| Property | Value | Description |
|----------|-------|-------------|
| ID | OpportunityStageForm | Unique identifier for the form control |
| DenyAdd | false | Allows users to add new opportunity stages |
| DenyDelete | false | Allows users to delete opportunity stages |
| DenyEdit | false | Allows users to edit opportunity stages |
| KeyColumn | opportunity_stage_id | The primary key column in the database table |
| PageSize | 10 | Number of records displayed per page |
| Width | 1000 | Width of the form in pixels |
| TableSchema | crm | Database schema name containing the table |
| Table | opportunity_stages | Database table name |
| ViewSchema | crm | Database schema name containing the view |
| View | opportunity_stages | Database view name used for displaying data |
| Text | <%$Resources:Titles, OpportunityStages %> | The title of the form, retrieved from resource files |

The form control is a custom server control, likely defined in [FormControl.ascx](../../UserControls/Forms/FormControl.ascx.md) which provides a standardized interface for database CRUD operations throughout the application.

## Database Integration

The page interacts with the following database objects:

- **Table**: `crm.opportunity_stages` - Stores the opportunity stage data
- **View**: `crm.opportunity_stages` - View used for displaying opportunity stage data

## Localization

The page uses resource files for localization:
- The form title is retrieved from the `Titles` resource file using the key `OpportunityStages`

## Related Components

- [CRM/Setup/LeadStatuses.aspx](./LeadStatuses.aspx.md) - For managing lead statuses
- [CRM/Setup/LeadSources.aspx](./LeadSources.aspx.md) - For managing lead sources
- [CRM/Opportunity.aspx](../Opportunity.aspx.md) - Page that uses opportunity stages for opportunity management
- [CRM/OpportunityFollowup.aspx](../OpportunityFollowup.aspx.md) - For following up on opportunities

## User Permissions

This page allows full CRUD operations as all "Deny" properties are set to false. However, actual user access would depend on the application's security model and the user's role-based permissions.

## Usage

This page would typically be accessed by CRM administrators or sales managers who need to define or modify the stages that opportunities go through in the sales pipeline (e.g., Prospecting, Qualification, Proposal, Negotiation, Closed Won, Closed Lost).

Maintaining proper opportunity stages is critical for:
- Tracking sales pipeline progress
- Forecasting sales
- Analyzing conversion rates between stages
- Standardizing the sales process across the organization
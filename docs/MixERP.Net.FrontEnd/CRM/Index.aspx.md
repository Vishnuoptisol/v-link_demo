# MixERP.Net.FrontEnd\CRM\Index.aspx.cs Documentation

## Overview
This file defines the `Index` class that serves as the code-behind for the CRM Index page in the MixERP.Net application. The class inherits from `MixERP.Net.BusinessLayer.BasePageClass` and is responsible for loading and displaying the appropriate menu structure for the CRM module.

## Class Documentation

### Index
**Namespace:** `MixERP.Net.FrontEnd.CRM`  
**Inherits from:** `MixERP.Net.BusinessLayer.BasePageClass`  
**Access Modifier:** `public partial`

This class represents the code-behind logic for the CRM Index page. As a partial class, it works in conjunction with the designer-generated code in [`Index.aspx.designer.cs`](MixERP.Net.FrontEnd/CRM/Index.aspx.designer.cs).

#### Attributes
- `MenuLiteral`: An implicit control defined in the associated `.aspx` file, which will display the menu HTML.

## Method Documentation

### Page_Load
**Access Modifier:** `protected`  
**Return Type:** `void`  
**Parameters:**
- `sender` (object): The object that raised the event.
- `e` (EventArgs): The event arguments.

This method is automatically called when the page loads. It retrieves the appropriate menu for the current page and assigns it to the `MenuLiteral` control for rendering.

#### Implementation Steps:
1. Calls `MixERP.Net.BusinessLayer.Helpers.MenuHelper.GetPageMenu()` with the current page as a parameter.
2. Assigns the returned menu HTML to the `Text` property of the `MenuLiteral` control.

#### Example Usage:
This method is not called directly by developers; it's part of the ASP.NET page lifecycle and is automatically invoked when the page is loaded.

```csharp
// This happens automatically when the page loads
protected void Page_Load(object sender, EventArgs e)
{
    string menu = MixERP.Net.BusinessLayer.Helpers.MenuHelper.GetPageMenu(this.Page);
    MenuLiteral.Text = menu;
}
```

## Related Files
This file is part of the CRM module in MixERP.Net.FrontEnd:
- [`Index.aspx`](MixERP.Net.FrontEnd/CRM/Index.aspx) - The web form associated with this code-behind file
- [`Index.aspx.designer.cs`](MixERP.Net.FrontEnd/CRM/Index.aspx.designer.cs) - The designer-generated code that defines the controls for this page

Other related CRM module files include:
- [`Lead.aspx.cs`](MixERP.Net.FrontEnd/CRM/Lead.aspx.cs)
- [`Opportunity.aspx.cs`](MixERP.Net.FrontEnd/CRM/Opportunity.aspx.cs)
- [`LeadFollowup.aspx.cs`](MixERP.Net.FrontEnd/CRM/LeadFollowup.aspx.cs)
- [`OpportunityFollowup.aspx.cs`](MixERP.Net.FrontEnd/CRM/OpportunityFollowup.aspx.cs)
- [`ConvertLeadToOpportunity.aspx.cs`](MixERP.Net.FrontEnd/CRM/ConvertLeadToOpportunity.aspx.cs)

## License
This code is licensed under the Mozilla Public License, v. 2.0. The full license text can be obtained at http://mozilla.org/MPL/2.0/.
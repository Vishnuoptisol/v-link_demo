# SignIn.aspx.designer.cs Documentation

## Overview

This file contains the auto-generated designer code for the SignIn class in the MixERP.Net.FrontEnd namespace. The designer file defines UI controls that are used in the [SignIn.aspx](SignIn.aspx.md) page, which serves as the authentication entry point for the MixERP application. This designer class is a partial class that complements the code-behind file [SignIn.aspx.cs](SignIn.aspx.cs.md), where the actual logic for these controls is implemented.

## Class Documentation

### SignIn

**Namespace**: `MixERP.Net.FrontEnd`  
**Type**: `public partial class`  
**Purpose**: Represents the designer portion of the sign-in page, containing declarations for all UI controls used on the page.

#### Attributes

The class contains several protected fields that represent UI controls on the sign-in form:

| Control Name | Type | Purpose |
|-------------|------|---------|
| `form1` | `System.Web.UI.HtmlControls.HtmlForm` | The main HTML form container for the sign-in page |
| `SignInLiteral` | `System.Web.UI.WebControls.Literal` | Displays the sign-in header text |
| `UserIdLiteral` | `System.Web.UI.WebControls.Literal` | Displays the label for the user ID field |
| `UserIdTextBox` | `System.Web.UI.WebControls.TextBox` | Input field for entering user ID |
| `PasswordLiteral` | `System.Web.UI.WebControls.Literal` | Displays the label for the password field |
| `PasswordTextBox` | `System.Web.UI.WebControls.TextBox` | Input field for entering password |
| `SelectBranchLiteral` | `System.Web.UI.WebControls.Literal` | Displays the label for branch selection |
| `BranchDropDownList` | `System.Web.UI.WebControls.DropDownList` | Dropdown list for selecting a branch office |
| `ObjectDataSource1` | `System.Web.UI.WebControls.ObjectDataSource` | Data source for populating the branch dropdown |
| `RememberMe` | `System.Web.UI.WebControls.CheckBox` | Checkbox for "Remember Me" functionality |
| `MessageLiteral` | `System.Web.UI.WebControls.Literal` | Displays messages (like error messages) to the user |
| `SignInButton` | `System.Web.UI.WebControls.Button` | Button to submit the sign-in form |
| `CantAccessAccountLinkButton` | `System.Web.UI.WebControls.LinkButton` | Link for account recovery options |

## Related Files

- [SignIn.aspx](SignIn.aspx.md) - The ASPX page that contains the HTML markup for the sign-in page
- [SignIn.aspx.cs](SignIn.aspx.cs.md) - The code-behind file containing the logic for the sign-in functionality
- [MixERPMaster.Master](MixERPMaster.Master.md) - The master page that likely provides the layout for the sign-in page

## Notes

1. This is an auto-generated file created by Visual Studio's ASP.NET Web Forms designer.
2. Direct modifications to this file are not recommended as they will be overwritten when the designer updates the file.
3. Any changes to control functionality should be made in the code-behind file ([SignIn.aspx.cs](SignIn.aspx.cs.md)) instead.
4. The control declarations in this file allow the code-behind file to access and manipulate these UI elements.

This file is part of the authentication module in the MixERP system, working alongside other account-related pages like [Account/SignOut.aspx](Account/SignOut.aspx.md) and [Account/ChangePassword.aspx](Account/ChangePassword.aspx.md).
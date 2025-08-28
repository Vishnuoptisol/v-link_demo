# SignIn.aspx.cs Documentation

## Overview

`SignIn.aspx.cs` is the code-behind file for the SignIn page in the MixERP.Net.FrontEnd application. This class handles user authentication, including processing login credentials, managing user sessions, and redirecting authenticated users to the dashboard. The file implements essential security features for the MixERP application's authentication system.

## Class Documentation

### SignIn

**Namespace**: `MixERP.Net.FrontEnd`  
**Inherits from**: `System.Web.UI.Page`  
**Access Modifier**: `public partial`

This class handles the sign-in functionality of the MixERP application. It manages authentication, session creation, and redirect logic for users.

## Method Documentation

### Page_Load

**Access Modifier**: `protected`  
**Return Type**: `void`  
**Parameters**:
- `sender` (object): The source of the event
- `e` (EventArgs): Event data

**Description**:
This method executes when the page loads and performs the following operations:
1. Sets focus to the UserIdTextBox for improved user experience
2. Checks if the user is already authenticated
3. If authenticated, retrieves the user identity
4. Verifies if a session already exists for the user
5. If no session exists, creates a new session
6. Redirects authenticated users to the Dashboard

**Example Usage**:
This method is automatically called by the ASP.NET page lifecycle when the page is loaded.

```csharp
// Called automatically during page load
protected void Page_Load(object sender, EventArgs e)
{
    // Method implementation
}
```

### SignInButton_Click

**Access Modifier**: `protected`  
**Return Type**: `void`  
**Parameters**:
- `sender` (object): The source of the event
- `e` (EventArgs): Event data

**Description**:
This method handles the sign-in button click event and performs the following operations:
1. Retrieves the selected office ID from the BranchDropDownList
2. Attempts to authenticate the user using credentials from the form
3. Creates a user session if authentication is successful
4. Displays an error message if authentication fails

**Example Usage**:
This method is automatically called when the sign-in button is clicked.

```csharp
// Called when the sign-in button is clicked
protected void SignInButton_Click(object sender, EventArgs e)
{
    // Method implementation
}
```

## Dependencies

This class depends on the following components:

1. **MixERP.Net.Common.Conversion**: Used for type casting through the `TryCastString` and `TryCastInteger` methods.

2. **MixERP.Net.BusinessLayer.Security.User**: Provides authentication functionality through its `SignIn` and `SetSession` methods.

3. **Resources.Warnings**: Contains localized warning messages, including `UserIdOrPasswordIncorrect`.

4. **UI Controls**: 
   - `UserIdTextBox`: Text box for entering user ID
   - `PasswordTextBox`: Text box for entering password
   - `BranchDropDownList`: Dropdown list for selecting office/branch
   - `RememberMe`: Checkbox for "Remember Me" functionality
   - `MessageLiteral`: Literal control for displaying error messages

5. **Page Elements**:
   - `Dashboard/Index.aspx`: The page to redirect to after successful authentication

## Authentication Flow

1. User enters credentials (user ID and password) and selects an office/branch
2. Upon form submission, the system validates credentials against the database
3. If authentication succeeds:
   - A session is created for the user
   - User is redirected to the dashboard
4. If authentication fails:
   - An error message is displayed
   - User remains on the login page

The authentication process uses a combination of Forms Authentication (evident from the `User.Identity.IsAuthenticated` check) and custom session management through the MixERP business layer.
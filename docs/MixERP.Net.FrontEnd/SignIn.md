# SignIn.aspx Documentation

## Overview
`SignIn.aspx` is the authentication entry point for the MixERP application. It provides a user interface for users to enter their credentials (user ID and password), select a branch office, and sign into the system. The page includes form validation and remember-me functionality.

## Page Structure

### Page Directives
- **Language**: C#
- **AutoEventWireup**: true
- **CodeBehind**: [SignIn.aspx.cs](SignIn.aspx.cs.md)
- **Inherits**: MixERP.Net.FrontEnd.SignIn

### External Resources
- CSS: `themes/purple/main.css`
- JavaScript: `Scripts/jquery.min.js` from the [Scripts](Scripts/jquery.min.md) directory
- Logo Image: `themes/purple/mixerp-logo.png`

### Form Elements

#### Layout
The sign-in form is organized with a logo section at the top and a sign-in form below. The form elements are arranged in a table layout for alignment.

#### Form Controls
1. **User ID Input**
   - **Control Type**: TextBox
   - **ID**: UserIdTextBox
   - **Label**: Localized "UserId" from resources

2. **Password Input**
   - **Control Type**: TextBox
   - **ID**: PasswordTextBox
   - **TextMode**: Password
   - **Label**: Localized "Password" from resources

3. **Branch Selection**
   - **Control Type**: DropDownList
   - **ID**: BranchDropDownList
   - **DataSource**: ObjectDataSource1
   - **DataTextField**: office_name
   - **DataValueField**: office_id
   - **Label**: Localized "SelectYourBranch" from resources

4. **Remember Me Option**
   - **Control Type**: CheckBox
   - **ID**: RememberMe
   - **Text**: Localized "RememberMe" from resources

5. **Message Display**
   - **Control Type**: Literal
   - **ID**: MessageLiteral

6. **Sign In Button**
   - **Control Type**: Button
   - **ID**: SignInButton
   - **Text**: Localized "SignIn" from resources
   - **Event**: OnClick="SignInButton_Click"

7. **Account Recovery**
   - **Control Type**: LinkButton
   - **ID**: CantAccessAccountLinkButton
   - **Text**: Localized "CantAccessAccount" from resources

### Data Sources
- **ObjectDataSource**
  - **ID**: ObjectDataSource1
  - **SelectMethod**: GetOffices
  - **TypeName**: MixERP.Net.BusinessLayer.Office.Offices
  - **Purpose**: Populates the branch dropdown with available offices

## Functionality

### Authentication Process
When the user submits the form by clicking the Sign In button, the `SignInButton_Click` method in [SignIn.aspx.cs](SignIn.aspx.cs.md) is triggered. This method handles:
1. Validation of user credentials
2. Authentication against the database
3. Creation of user session
4. Redirection to the appropriate page upon successful authentication
5. Display of error messages on authentication failure

### Default Values
The page includes a JavaScript section that pre-fills the form with test credentials:
```javascript
$("#UserIdTextBox").val('binod');
$("#PasswordTextBox").val('binod');
```
These default values are likely for development or testing purposes.

### Localization
The page uses ASP.NET's resource-based localization system for labels and messages. Resources are loaded from the `App_GlobalResources` folder using expressions like `<%$Resources:Titles, SignIn %>`.

### User Experience
1. User enters their ID and password
2. User selects their branch from the dropdown
3. User can opt to be remembered by checking the "Remember Me" box
4. Upon submission, the user is either authenticated and redirected or shown an error message
5. A "Can't access account" link is provided for account recovery options

## Dependencies
- **Resource Files**: The page references resources from the [App_GlobalResources](App_GlobalResources/) directory
- **Code Behind**: [SignIn.aspx.cs](SignIn.aspx.cs.md) contains the server-side logic
- **Business Layer**: Uses the MixERP.Net.BusinessLayer.Office.Offices class to retrieve office information

## Security Considerations
- The password field properly uses `TextMode="Password"` to mask input
- Authentication logic is handled server-side in the code-behind file
- The page uses HTTPS (implied by best practices, though not explicitly shown in the markup)
- Default credentials in the JavaScript section should be removed in production

## Notes
- The page uses a traditional WebForms approach with server controls
- The form includes a remember-me feature for persistent authentication
- The UI includes proper labeling and a clean layout for good user experience
- Default test credentials are hardcoded in client-side script, which is not recommended for production environments
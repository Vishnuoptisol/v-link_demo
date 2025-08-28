# SignOut.aspx.cs Documentation

## Overview

This file implements the sign-out functionality for the MixERP.Net web application. It handles the process of signing out users by removing their session information, invalidating authentication cookies, and redirecting them to the sign-in page. The class extends [BasePageClass](../BusinessLayer/BasePageClass.md), which provides common functionality for pages in the application.

## Class Documentation

### SignOut

- **Namespace**: `MixERP.Net.FrontEnd.Account`
- **Parent Class**: `MixERP.Net.BusinessLayer.BasePageClass`
- **Access Modifier**: `public`
- **Purpose**: Handles the user sign-out process in the MixERP application

## Method Documentation

### Page_Load

- **Access Modifier**: `protected`
- **Return Type**: `void`
- **Parameters**:
  - `sender`: `object` - The source of the event
  - `e`: `EventArgs` - Event data associated with the Page_Load event

- **Purpose**: Executes when the page loads to perform the sign-out process

- **Step-by-step Explanation**:
  1. Removes the "UserName" key from the current session using `Session.Remove("UserName")`
  2. Calls the `FormsAuthentication.SignOut()` method to invalidate the authentication cookie
  3. Redirects the user to the sign-in page using `Response.Redirect("~/SignIn.aspx")`

- **Example Usage**:
  This method is automatically called when the SignOut.aspx page is loaded in the browser. It is not typically called directly from other code.

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    Session.Remove("UserName");
    FormsAuthentication.SignOut();
    Response.Redirect("~/SignIn.aspx");
}
```

## Dependencies

- **System.Web.Security**: Used for forms authentication functionality via the `FormsAuthentication` class
- **System.Web.UI**: Provides the base Page class and UI components
- **MixERP.Net.BusinessLayer.BasePageClass**: The parent class that this page inherits from
- **[SignIn.aspx](../SignIn.aspx.md)**: The page that users are redirected to after signing out

## Related Files

- **[SignOut.aspx](SignOut.aspx.md)**: The associated ASPX file for this code-behind
- **[SignOut.aspx.designer.cs](SignOut.aspx.designer.cs.md)**: The designer file that defines UI components

## Notes

- The sign-out process is straightforward and follows standard web application practices:
  1. Clear session data
  2. Sign out from the authentication system
  3. Redirect to the login page
- No additional validation or confirmation is performed before signing out the user
- This implementation uses ASP.NET's Forms Authentication system rather than modern identity frameworks
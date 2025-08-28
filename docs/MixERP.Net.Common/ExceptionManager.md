# ExceptionManager.cs Documentation

## Overview

`ExceptionManager.cs` is a utility class in the MixERP.Net.Common namespace that provides centralized exception handling functionality for the MixERP application. It offers a mechanism to handle exceptions, store them in the current session, and redirect users to an error page, ensuring a consistent error handling approach across the application.

## Class Documentation

### ExceptionManager

**Type:** Static Class  
**Access Modifier:** Public  
**Namespace:** MixERP.Net.Common

This static utility class provides methods for handling exceptions in a standardized way across the MixERP application. It serves as a central point for exception handling, allowing for consistent error presentation to users and potential logging of exceptions.

## Method Documentation

### HandleException

**Access Modifier:** Public  
**Return Type:** void  
**Parameters:**
- `ex` (System.Exception): The exception to be handled.

**Description:**  
The `HandleException` method processes an exception by:

1. Checking if the provided exception is null, returning early if it is.
2. Retrieving the base exception (the original exception that caused the current exception) if available.
3. Storing the exception in the current HTTP session for later retrieval.
4. Redirecting the user to the application's runtime error page.

This method ensures that when exceptions occur, users are directed to a friendly error page rather than seeing raw exception details, while also preserving the exception information for debugging purposes.

**Step-by-Step Explanation:**
1. If the exception parameter is null, the method returns without taking any action.
2. The method attempts to get the base exception using `GetBaseException()` to identify the root cause.
3. The method checks if the current HTTP context session is available.
4. If a valid session exists, the exception is stored in the session with the key "ex".
5. The user is redirected to the "~/RuntimeError.aspx" page with a complete redirect (setting the second parameter to true).

**Example Usage:**
```csharp
try
{
    // Code that might throw an exception
    int result = 10 / 0; // This will throw a DivideByZeroException
}
catch (Exception ex)
{
    ExceptionManager.HandleException(ex);
    // Execution will not continue past this point due to the redirect
}
```

## Related Files

The `ExceptionManager` class works in conjunction with other files in the MixERP application:

- The exception handling process redirects to "~/RuntimeError.aspx", which is responsible for displaying user-friendly error messages.
- The class operates within the MixERP.Net.Common namespace, which contains other utility classes for the MixERP application.

## Dependencies

The class utilizes the following .NET Framework namespaces:
- System
- System.Collections.Generic
- System.Linq
- System.Text
- System.Web

The class depends on the HttpContext.Current to access the session state and perform redirects, making it suitable for web applications but requiring modification for use in other contexts.
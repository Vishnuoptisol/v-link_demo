# Global.asax.cs Documentation

## Overview

The `Global.asax.cs` file serves as the application entry point for the MixERP.Net.FrontEnd web application. It handles application-wide events, such as application start, error handling, and session management. The file primarily configures URL routing to direct users to the appropriate pages within the application and manages error handling at the application level.

## Class Documentation

### Global

**Namespace**: `MixERP.Net.FrontEnd`
**Inherits From**: `System.Web.HttpApplication`
**Access Modifier**: `public`

This class handles application-level events and global configurations for the MixERP web application.

## Method Documentation

### Application_Start

**Access Modifier**: `void` (implicit private)
**Parameters**:
- `sender` (object): The source of the event.
- `e` (EventArgs): Event data.
**Return Type**: `void`

This method is automatically called when the application starts. It initializes the application by registering routing rules.

**Step by Step**:
1. Calls the `RegisterRoutes` method, passing the system's `RouteTable.Routes` collection.

**Example Usage**:
This method is called automatically by the ASP.NET runtime and is not typically invoked directly.

### RegisterRoutes

**Access Modifier**: `protected static`
**Parameters**:
- `routes` (RouteCollection): The collection of routes to register.
**Return Type**: `void`

Sets up URL routing for the application by defining URL patterns and their corresponding page handlers.

**Step by Step**:
1. Checks if the provided routes collection is not null.
2. Maps the default route ("") to the SignIn page (`~/SignIn.aspx`).
3. Maps a reporting route pattern ("Reports/{path}") to the ReportMaster page (`~/Reports/ReportMaster.aspx`).

**Example Usage**:
```csharp
RegisterRoutes(RouteTable.Routes);
```

### Application_End

**Access Modifier**: `void` (implicit private)
**Parameters**:
- `sender` (object): The source of the event.
- `e` (EventArgs): Event data.
**Return Type**: `void`

Called when the application is shutting down. Currently contains no implementation.

**Step by Step**:
1. No steps are implemented, only contains a comment.

**Example Usage**:
This method is called automatically by the ASP.NET runtime when the application shuts down.

### Application_Error

**Access Modifier**: `void` (implicit private)
**Parameters**:
- `sender` (object): The source of the event.
- `e` (EventArgs): Event data.
**Return Type**: `void`

Handles unhandled exceptions that occur within the application.

**Step by Step**:
1. Retrieves the last error that occurred using `Server.GetLastError()`.
2. If there is no error, exits the method.
3. If the error is a `ThreadAbortException`, exits the method (as these are often part of normal page redirects).
4. Otherwise, calls `MixERP.Net.Common.ExceptionManager.HandleException()` to process the exception.

**Example Usage**:
This method is called automatically by the ASP.NET runtime when an unhandled exception occurs.

### Session_Start

**Access Modifier**: `void` (implicit private)
**Parameters**:
- `sender` (object): The source of the event.
- `e` (EventArgs): Event data.
**Return Type**: `void`

Called when a new user session begins. Currently contains no implementation.

**Step by Step**:
1. No steps are implemented, only contains a comment.

**Example Usage**:
This method is called automatically by the ASP.NET runtime when a new user session starts.

### Session_End

**Access Modifier**: `void` (implicit private)
**Parameters**:
- `sender` (object): The source of the event.
- `e` (EventArgs): Event data.
**Return Type**: `void`

Called when a user session ends. Currently contains no implementation.

**Step by Step**:
1. No steps are implemented, only contains comments.
2. The comment notes that this event is only raised when session state mode is set to InProc in Web.config.

**Example Usage**:
This method is called automatically by the ASP.NET runtime when a user session ends (with the noted configuration requirement).

## Dependencies

The class depends on the following components:

- Standard .NET libraries:
  - `System`
  - `System.Collections.Generic`
  - `System.Linq`
  - `System.Web`
  - `System.Web.Routing`
  - `System.Web.Security`
  - `System.Web.SessionState`

- MixERP Components:
  - `MixERP.Net.Common.ExceptionManager`: Used for handling exceptions in the application.

- Related files:
  - [SignIn.aspx](SignIn.aspx.md): The default landing page for the application.
  - [Reports/ReportMaster.aspx](Reports/ReportMaster.aspx.md): The page handling report rendering.

## Routing Configuration

The application defines two main routes:

1. **Default Route**:
   - Pattern: "" (empty string/root URL)
   - Handler: `~/SignIn.aspx`
   - Purpose: Directs users to the sign-in page when they access the application root.

2. **Reporting Route**:
   - Pattern: "Reports/{path}"
   - Handler: `~/Reports/ReportMaster.aspx`
   - Purpose: Handles all reporting URLs, where {path} is a parameter passed to the report master page.
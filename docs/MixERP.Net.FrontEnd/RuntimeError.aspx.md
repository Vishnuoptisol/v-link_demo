# RuntimeError.aspx.cs Documentation

## Overview

The `RuntimeError.aspx.cs` file is a code-behind file for the `RuntimeError.aspx` page in the MixERP.Net.FrontEnd application. It handles the display of runtime errors that occur during application execution. This class selectively displays error information based on the environment (development or production) and configuration settings.

## Class Documentation

### RuntimeError

**Purpose**: Manages the display of runtime error information to users.

**Access Modifier**: `public`

**Inheritance**: Inherits from `MixERP.Net.BusinessLayer.BasePageClass`

## Method Documentation

### Page_Load

**Purpose**: Handles the page load event and determines whether to display error details based on the environment and configuration.

**Access Modifier**: `protected`

**Parameters**:
- `sender` (object): The source of the event.
- `e` (EventArgs): An EventArgs object containing event data.

**Return Type**: `void`

**Implementation Details**:
1. Retrieves the server software information from the request variables.
2. If server information is empty (indicating development environment in Visual Studio), displays the error details.
3. Otherwise, checks the "DisplayError" setting in the application configuration:
   - If set to "true", displays error details.
   - If set to any other value, hides detailed error information.

**Example Usage**:
```csharp
// This method is automatically called during page load
protected void Page_Load(object sender, EventArgs e)
{
    // Method implementation
}
```

### DisplayError

**Purpose**: Retrieves the exception stored in the session and formats it for display on the page.

**Access Modifier**: `private`

**Parameters**: None

**Return Type**: `void`

**Implementation Details**:
1. Retrieves the exception object stored in the session with the key "ex".
2. If an exception exists:
   - Creates a StringBuilder to construct the HTML for the error display.
   - Adds a horizontal rule for visual separation.
   - Formats and adds the exception message as a heading (h2).
   - Sets the constructed HTML to the ExceptionLiteral control on the page.

**Example Usage**:
```csharp
// This method is called internally
private void DisplayError()
{
    // Method implementation
}
```

## Related Files

This class is part of the error handling system and works with:
- [RuntimeError.aspx](RuntimeError.aspx.md) - The ASPX page that displays the error information
- [RuntimeError.aspx.designer.cs](RuntimeError.aspx.designer.cs.md) - Contains the designer-generated code for the page controls

## Dependencies

- Uses [Global.asax.cs](Global.asax.cs.md) indirectly for application-wide error handling
- Inherits from the `BasePageClass` in the MixERP.Net.BusinessLayer namespace
- Utilizes `System.Configuration.ConfigurationManager` to read application settings from [Web.config](Web.config.md)

## Configuration

The error display behavior can be configured via the "DisplayError" setting in the [Web.config](Web.config.md) file:
```xml
<appSettings>
  <add key="DisplayError" value="true" />
</appSettings>
```

When set to "true", detailed error information is displayed even in production environments.